# Migrating Existing Links to CloudFront CDN

Old Host: gc-www-media.s3.us-west-1.amazonaws.com
New Host: dqyd9zmozp168.cloudfront.net

Test Links:

- https://gc-www-media.s3.us-west-1.amazonaws.com/GC_Logo_Black_0b6688308c.png
- https://dqyd9zmozp168.cloudfront.net/GC_Logo_Black_0b6688308c.png
- https://cdn.getcommunity.com/GC_Logo_Black_0b6688308c.png

## First Identify All the Table Columns That Store S3 Links

```sql
-- 1) Create a place to store matches
DROP TABLE IF EXISTS temp_value_hits;
CREATE TEMP TABLE temp_value_hits (
  table_schema text,
  table_name   text,
  column_name  text,
  sample_ctid  tid
);

-- 2) Scan the database
DO $$
DECLARE
  r RECORD;
  search_text text := 'gc-www-media.s3.us-west-1.amazonaws.com';
  sql text;
BEGIN
  FOR r IN
    SELECT c.table_schema, c.table_name, c.column_name
    FROM information_schema.columns c
    WHERE c.table_schema NOT IN ('pg_catalog', 'information_schema')
      AND c.data_type IN ('text', 'character varying', 'character', 'json', 'jsonb')
  LOOP
    sql := format(
      'INSERT INTO temp_value_hits(table_schema, table_name, column_name, sample_ctid)
       SELECT %L, %L, %L, t.ctid
       FROM %I.%I t
       WHERE t.%I::text LIKE %L
       LIMIT 1',
      r.table_schema, r.table_name, r.column_name,
      r.table_schema, r.table_name,
      r.column_name,
      '%' || search_text || '%'
    );

    BEGIN
      EXECUTE sql;
    EXCEPTION
      WHEN undefined_table OR undefined_column THEN
        -- schema drift / concurrent changes
        NULL;
      WHEN others THEN
        -- ignore casting/permission oddities
        NULL;
    END;
  END LOOP;
END $$;

-- 3) View results
SELECT * FROM temp_value_hits
ORDER BY table_schema, table_name, column_name;
```

## Then Update Each Column Individually

```sql
/*
  Hostname substring replace across 4 known targets.

  OLD: gc-www-media.s3.us-west-1.amazonaws.com
  NEW: dqyd9zmozp168.cloudfront.net

  Run #1: ends with ROLLBACK; (no permanent changes, but you still see NOTICE row counts)
  Run #2: change ROLLBACK; -> COMMIT; (applies changes)

  Notes:
  - Does NOT touch http/https (only hostname substring)
  - JSON/JSONB columns are updated via text replace then cast back
*/

-- =========================
-- 0) Config
-- =========================
DO $$
BEGIN
  IF 'gc-www-media.s3.us-west-1.amazonaws.com' = 'dqyd9zmozp168.cloudfront.net' THEN
    RAISE EXCEPTION 'Old and new values are identical; aborting.';
  END IF;
END $$;

-- =========================
-- 1) DRY-RUN REPORT (no writes)
-- =========================
SELECT
  'public.components_shared_rich_text_blocks' AS table_name,
  'content' AS column_name,
  COUNT(*) AS rows_matching
FROM public.components_shared_rich_text_blocks
WHERE content::text LIKE '%gc-www-media.s3.us-west-1.amazonaws.com%'

UNION ALL
SELECT
  'public.files' AS table_name,
  'formats' AS column_name,
  COUNT(*) AS rows_matching
FROM public.files
WHERE formats::text LIKE '%gc-www-media.s3.us-west-1.amazonaws.com%'

UNION ALL
SELECT
  'public.files' AS table_name,
  'url' AS column_name,
  COUNT(*) AS rows_matching
FROM public.files
WHERE url::text LIKE '%gc-www-media.s3.us-west-1.amazonaws.com%'

UNION ALL
SELECT
  'public.strapi_core_store_settings' AS table_name,
  'value' AS column_name,
  COUNT(*) AS rows_matching
FROM public.strapi_core_store_settings
WHERE value::text LIKE '%gc-www-media.s3.us-west-1.amazonaws.com%'
ORDER BY table_name, column_name;

-- Sample previews
SELECT
  'public.components_shared_rich_text_blocks' AS table_name,
  'content' AS column_name,
  ctid,
  LEFT(content::text, 300) AS sample_before
FROM public.components_shared_rich_text_blocks
WHERE content::text LIKE '%gc-www-media.s3.us-west-1.amazonaws.com%'
LIMIT 5;

SELECT
  'public.files' AS table_name,
  'formats' AS column_name,
  ctid,
  LEFT(formats::text, 300) AS sample_before
FROM public.files
WHERE formats::text LIKE '%gc-www-media.s3.us-west-1.amazonaws.com%'
LIMIT 5;

SELECT
  'public.files' AS table_name,
  'url' AS column_name,
  ctid,
  LEFT(url::text, 300) AS sample_before
FROM public.files
WHERE url::text LIKE '%gc-www-media.s3.us-west-1.amazonaws.com%'
LIMIT 5;

SELECT
  'public.strapi_core_store_settings' AS table_name,
  'value' AS column_name,
  ctid,
  LEFT(value::text, 300) AS sample_before
FROM public.strapi_core_store_settings
WHERE value::text LIKE '%gc-www-media.s3.us-west-1.amazonaws.com%'
LIMIT 5;

-- =========================
-- 2) UPDATE TRANSACTION
-- =========================
BEGIN;

DO $$
DECLARE
  old_host text := 'gc-www-media.s3.us-west-1.amazonaws.com';
  new_host text := 'dqyd9zmozp168.cloudfront.net';

  targets text[][3] := ARRAY[
    ARRAY['public','components_shared_rich_text_blocks','content'],
    ARRAY['public','files','formats'],
    ARRAY['public','files','url'],
    ARRAY['public','strapi_core_store_settings','value']
  ];

  i int;
  t_schema text;
  t_table  text;
  t_col    text;

  col_type text;
  sql text;
  updated_count bigint;
BEGIN
  FOR i IN 1..array_length(targets, 1) LOOP
    t_schema := targets[i][1];
    t_table  := targets[i][2];
    t_col    := targets[i][3];

    SELECT c.data_type
      INTO col_type
    FROM information_schema.columns c
    WHERE c.table_schema = t_schema
      AND c.table_name   = t_table
      AND c.column_name  = t_col;

    IF col_type IS NULL THEN
      RAISE EXCEPTION 'Could not find %.%.% in information_schema.columns', t_schema, t_table, t_col;
    END IF;

    IF col_type = 'jsonb' THEN
      sql := format(
        'UPDATE %I.%I
         SET %I = CASE WHEN %I IS NULL THEN NULL ELSE replace(%I::text, %L, %L)::jsonb END
         WHERE %I::text LIKE %L',
        t_schema, t_table,
        t_col, t_col, t_col, old_host, new_host,
        t_col, '%' || old_host || '%'
      );
    ELSIF col_type = 'json' THEN
      sql := format(
        'UPDATE %I.%I
         SET %I = CASE WHEN %I IS NULL THEN NULL ELSE replace(%I::text, %L, %L)::json END
         WHERE %I::text LIKE %L',
        t_schema, t_table,
        t_col, t_col, t_col, old_host, new_host,
        t_col, '%' || old_host || '%'
      );
    ELSE
      sql := format(
        'UPDATE %I.%I
         SET %I = CASE WHEN %I IS NULL THEN NULL ELSE replace(%I::text, %L, %L) END
         WHERE %I::text LIKE %L',
        t_schema, t_table,
        t_col, t_col, t_col, old_host, new_host,
        t_col, '%' || old_host || '%'
      );
    END IF;

    EXECUTE sql;
    GET DIAGNOSTICS updated_count = ROW_COUNT;

    RAISE NOTICE 'Updated % rows in %.%.% (type=%)', updated_count, t_schema, t_table, t_col, col_type;
  END LOOP;
END $$;

-- =========================
-- 3) CHOOSE ONE
-- =========================
ROLLBACK;  -- Run #1 (safe): verifies NOTICE output, makes no permanent changes
-- COMMIT; -- Run #2 (real): apply changes

-- Optional post-check: after the COMMIT run, run this separately to confirm zeros.
-- SELECT 'public.files' AS table_name, 'url' AS column_name, COUNT(*) AS rows_still_matching
-- FROM public.files WHERE url::text LIKE '%gc-www-media.s3.us-west-1.amazonaws.com%';
```
