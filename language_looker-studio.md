# Looker Studio

## Regular Expressions

### Google Ads

```bash
# Session Campaign
REGEXP_EXTRACT(Final URL, "[?&]utm_campaign=([^&]+)")

# Session Content
REGEXP_EXTRACT(Final URL, "[?&]utm_content=([^&]+)")

# Session Creative Format
REGEXP_EXTRACT(Final URL, "[?&]utm_creative_format=([^&]+)")

# Session Medium
REGEXP_EXTRACT(Final URL, "[?&]utm_medium=([^&]+)")

# Session Source
REGEXP_EXTRACT(Final URL, "[?&]utm_source=([^&]+)")
```

### Facebook Ads

```bash
# Session Campaign
REGEXP_EXTRACT(Destination URL, "[?&]utm_campaign=([^&]+)")

# Session Content
REGEXP_EXTRACT(Destination URL, "[?&]utm_content=([^&]+)")

# Session Creative Format
REGEXP_EXTRACT(Destination URL, "[?&]utm_creative_format=([^&]+)")

# Session Medium
REGEXP_EXTRACT(Destination URL, "[?&]utm_medium=([^&]+)")

# Session Source
REGEXP_EXTRACT(Destination URL, "[?&]utm_source=([^&]+)")
```
