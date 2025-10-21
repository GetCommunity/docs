# S3 Bucket & Prefix Strategy

Buckets (by environment)

```plaintext
s3://gc-data-dev/
s3://gc-data-prod/
```

All clients live in the same env bucket (no strict isolation required right now).

## Top-level prefix (per client → zone)

```plantext
# <zone> = {raw, bronze, silver, gold}
s3://gc-data-<env>/clients/{client_code}/<zone>/

s3://gc-data-prod/clients/12345/raw/
s3://gc-data-prod/clients/12345/bronze/
s3://gc-data-prod/clients/12345/silver/
s3://gc-data-prod/clients/12345/gold/
```

## Media Platform Ad Type prefix (per client → zone)

```plantext
s3://gc-data-<env>/clients/{client_code}/<zone>/
    {platform_slug}/{media_type_slug}/

s3://gc-data-prod/clients/12345/raw/zillow/boosts/
s3://gc-data-prod/clients/12345/raw/nhs/listings/
s3://gc-data-prod/clients/12345/raw/realtor/listings/
s3://gc-data-prod/clients/12345/raw/realtor/native/
```

### RAW (landing) — optional but recommended

Purpose: keep verbatim source files exactly as received (CSV, XLSX, TXT, HTML, XML, etc.) for audit/backfill. You indicated RAW exists and may be mixed formats.

```plaintext
clients/{client_code}/raw/{platform_slug}/{media_type_slug}/
  year=yyyy/month=mm/
    ingest_dt=yyyy-mm-dd/
      <original-filenames>...
      _metadata.json
```

```plaintext
clients/olsonhomes/raw/zillow/boosts/
  year=2025/month=10/
    ingest_dt=2025-11-01/
      2025-10-insights.csv
      _metadata.json
```

### BRONZE — immutable, schema-on-read

Monthly manual loads; each ingestion job has its own folder (easy retry/backfill). Files are CSV or JSON. Primary partition by report_date (yyyy/mm/dd).

```plaintext
clients/{client_code}/bronze/{platform_slug}/{media_type_slug}/
  year=2025/month=10/
    ingest_dt=2025-11-01/
      yyyy-mm_{platform_slug}_{media_type_slug}.{json|csv}.gz
      _metadata.json
```

```plaintext
clients/olsonhomes/raw/zillow/boosts/
  year=2025/month=10/
    ingest_dt=2025-11-01/
      2025-10-insights.csv
      _metadata.json
```

### SILVER — cleaned & conformed (Parquet)

Schema-on-write; normalized types, consistent dimension keys; still partitioned by report_date. You prefer Parquet without a table format.

```plaintext
clients/{client_code}/silver/{platform_slug}/{media_type_slug}/
  year=2025/month=10/
    load_dt=yyyy-mm-dd/
      part-0000.parquet
      ...
```

```plaintext
clients/olsonhomes/silver/zillow/boosts/
  year=2025/month=10/
    load_dt=2025-11-01/
      part-0000.parquet
```

### GOLD — analytics-ready aggregates (Parquet)

Materialize facts for Looker Studio via Redshift Spectrum (and/or Redshift copies).

```plaintext
clients/{client_code}/gold/{subject_area}/
  table={table_name}/
    report_month=2025/10/
      part-*.parquet
```

```plaintext
clients/olsonhomes/gold/zillow/boosts/
  table=fct_monthly_zillow_boost_metrics/
    report_month=2025/10/
      part-0000.parquet
```

## Sidecar `_metadata.json` (monthly fields)

Add explicit period fields for clarity:

```json
{
  "client_code": "olsonhomes",
  "client_twid": "1234567890",
  "platform_slug": "zillow",
  "media_type_slug": "boosts",
  "report_month": "2025-10",
  "period_start": "2025-10-01",
  "period_end": "2025-10-31",
  "source_type": "api|manual",
  "api_endpoint": "insights",
  "ingestion_job_ts": "2025-11-01T03:00:00Z",
  "record_count": 12345,
  "byte_count": 9876543,
  "source_hash": "sha256:...",
  "status": "success|partial|failed",
  "notes": ""
}
```
