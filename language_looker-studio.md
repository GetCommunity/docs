# Looker Studio

## Regular Expressions

### Google Analytics

```plaintext
# GC Organic Traffic Net
(?i)gc-social|gc-blast|gc-flow|gc-signage|gc-content|gc-popup|gc-press_release|gc-pdf_content


# GC Paid Traffic Net
(?i)gc-paid|gc-flow|gc-signage|gc-paid_ctv|gc-popup|gc-press_release|gc-pdf_content
```

```bash
# Day of the Week
CASE
    WHEN WEEKDAY(Date) = 0 THEN "Sunday"
    WHEN WEEKDAY(Date) = 1 THEN "Monday"
    WHEN WEEKDAY(Date) = 2 THEN "Tuesday"
    WHEN WEEKDAY(Date) = 3 THEN "Wednesday"
    WHEN WEEKDAY(Date) = 4 THEN "Thursday"
    WHEN WEEKDAY(Date) = 5 THEN "Friday"
    WHEN WEEKDAY(Date) = 6 THEN "Saturday"
END

# Time
CASE
    WHEN Hour = "0" THEN "12 AM"
    WHEN Hour = "1" THEN "1 AM"
    WHEN Hour = "2" THEN "2 AM"
    WHEN Hour = "3" THEN "3 AM"
    WHEN Hour = "4" THEN "4 AM"
    WHEN Hour = "5" THEN "5 AM"
    WHEN Hour = "6" THEN "6 AM"
    WHEN Hour = "7" THEN "7 AM"
    WHEN Hour = "8" THEN "8 AM"
    WHEN Hour = "9" THEN "9 AM"
    WHEN Hour = "10" THEN "10 AM"
    WHEN Hour = "11" THEN "11 AM"
    WHEN Hour = "12" THEN "12 PM"
    WHEN Hour = "13" THEN "1 PM"
    WHEN Hour = "14" THEN "2 PM"
    WHEN Hour = "15" THEN "3 PM"
    WHEN Hour = "16" THEN "4 PM"
    WHEN Hour = "17" THEN "5 PM"
    WHEN Hour = "18" THEN "6 PM"
    WHEN Hour = "19" THEN "7 PM"
    WHEN Hour = "20" THEN "8 PM"
    WHEN Hour = "21" THEN "9 PM"
    WHEN Hour = "22" THEN "10 PM"
    WHEN Hour = "23" THEN "11 PM"
END

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
# Utm Campaign
REGEXP_EXTRACT(Destination URL, "[?&]utm_campaign=([^&]+)")

# Utm Content
REGEXP_EXTRACT(Destination URL, "[?&]utm_content=([^&]+)")

# Utm Medium
REGEXP_EXTRACT(Destination URL, "[?&]utm_medium=([^&]+)")

# Utm Source
REGEXP_EXTRACT(Destination URL, "[?&]utm_source=([^&]+)")

# Utm Creative Format
REGEXP_EXTRACT(Destination URL, "[?&]utm_creative_format=([^&]+)")

# Utm ID
REGEXP_EXTRACT(Destination URL, "[?&]utm_id=([^&]+)")
```

### Posted Time (PST)

- Posted Time (PST)
- AKA Date Time

```bash
# Facebook
DATETIME_SUB(Published, INTERVAL 7 HOUR)

# Instagram
DATETIME_SUB(Timestamp, INTERVAL 7 HOUR)

# X/Twitter
DATETIME_SUB(Date And Time, INTERVAL 7 HOUR)

# YouTube
DATETIME_SUB(Date, INTERVAL 7 HOUR)

# LinkedIn
DATETIME_SUB(Date And Time, INTERVAL 7 HOUR)
```

## Days Since Posted

Days Since Posted
Days Ago

```bash
# Facebook
DATE_DIFF(CURRENT_DATE(), Published)

# Instagram
DATE_DIFF(CURRENT_DATE(), Posted Time (PST))

# X/Twitter
DATE_DIFF(CURRENT_DATE(), Posted Time (PST))

# YouTube
DATE_DIFF(CURRENT_DATE(), Posted Time (PST))

# LinkedIn
DATE_DIFF(CURRENT_DATE(), Posted Time (PST))

# TikTok
DATE_DIFF(CURRENT_DATE(), Post Time)
```
