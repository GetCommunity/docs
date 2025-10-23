# Looker Studio

## Regular Expressions

### Google Analytics

```bash
# Week Value (text)
FORMAT_DATETIME('%m/%d/%Y', DATETIME_TRUNC(Date, WEEK))

# Week Date (Date)
PARSE_DATE("%m/%d/%Y", Week Value)

# Campaign Phase
CASE
  WHEN STARTS_WITH(Session Campaign Name, "p1-") THEN "Phase 1"
  WHEN STARTS_WITH(Session Campaign Name, "p2-") THEN "Phase 2"
  WHEN STARTS_WITH(Session Campaign Name, "p3-") THEN "Phase 3"
  WHEN STARTS_WITH(Session Campaign Name, "p4-") THEN "Phase 4"
  WHEN STARTS_WITH(Session Campaign Name, "p5-") THEN "Phase 5"
  WHEN STARTS_WITH(Session Campaign Name, "brand") THEN "Brand"
  ELSE "(not set)"
END

# Content Pillar
CASE
  WHEN STARTS_WITH(Session Manual Ad Content, "testimonial") THEN "Testimonials"
  WHEN STARTS_WITH(Session Manual Ad Content, "agent") THEN "Agent Videos"
  WHEN STARTS_WITH(Session Manual Ad Content, "education") THEN "Education"
  WHEN STARTS_WITH(Session Manual Ad Content, "charity") THEN "Charity"
  WHEN STARTS_WITH(Session Manual Ad Content, "recruitment") THEN "Recruitment"
  WHEN STARTS_WITH(Session Manual Ad Content, "lifestyle") THEN "Location/Lifestyle"
  WHEN STARTS_WITH(Session Manual Ad Content, "milestone") THEN "Milestone"
  WHEN STARTS_WITH(Session Manual Ad Content, "trends") THEN "Trends"
  WHEN STARTS_WITH(Session Manual Ad Content, "brand") THEN "Brand"
  WHEN STARTS_WITH(Session Manual Ad Content, "events") THEN "Events"
  WHEN STARTS_WITH(Session Manual Ad Content, "live_better") THEN "Live Better"
  WHEN STARTS_WITH(Session Manual Ad Content, "personalization") THEN "Personalization"
  WHEN STARTS_WITH(Session Manual Ad Content, "product") THEN "Product"
  WHEN STARTS_WITH(Session Manual Ad Content, "recipes") THEN "Recipes"
  WHEN STARTS_WITH(Session Manual Ad Content, "chefmolly") THEN "Chef Molly"
  WHEN STARTS_WITH(Session Manual Ad Content, "other") THEN "Other"
  ELSE "(not set)"
END
```

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

### Posted Time (PST)

- Posted Time (PST)
- AKA Date Time

```bash
# Facebook
DATETIME_SUB(Published, INTERVAL 7 HOUR)

# Instagram
DATETIME_SUB(Timestamp, INTERVAL 7 HOUR)

# LinkedIn
DATETIME_SUB(Date And Time, INTERVAL 7 HOUR)

# X/Twitter
DATETIME_SUB(Date And Time, INTERVAL 7 HOUR)

# YouTube
DATETIME_SUB(Date, INTERVAL 7 HOUR)
```
