# Looker Studio

## Regular Expressions

### GC Data Database

period

```bash
PARSE_DATE("%Y-%m", CONCAT(year, "-", month))
```

Date Month Start

```bash
PARSE_DATE("%m/1/%Y", CONCAT(Month, "/1/", Year))
```

date_hour

```bash
PARSE_DATETIME("%Y-%m-%d %H", FORMAT_DATETIME("%Y-%m-%d %H", publish_time))
```

Client

```bash
CASE
  WHEN teamwork_id = "187061" THEN "BIASC"
  WHEN teamwork_id = "173885" THEN "Brandywine Homes"
  WHEN teamwork_id = "124090" THEN "CDC Designs"
  WHEN teamwork_id = "146636" THEN "Chameleon Design"
  WHEN teamwork_id = "54883" THEN "Get Community Inc"
  WHEN teamwork_id = "1384180" THEN "Gold Key Development"
  WHEN teamwork_id = "1383643" THEN "Mayfair Communities"
  WHEN teamwork_id = "130123" THEN "Olson Homes"
  WHEN teamwork_id = "184891" THEN "Priest Ranch Winery"
  WHEN teamwork_id = "144048" THEN "River Islands"
  WHEN teamwork_id = "189976" THEN "Shea Carolina"
  WHEN teamwork_id = "168351" THEN "Shea Corporate"
  WHEN teamwork_id = "166962" THEN "Shea NorCal"
  WHEN teamwork_id = "158079" THEN "Shea San Diego"
  WHEN teamwork_id = "55100" THEN "Shea SoCal"
  WHEN teamwork_id = "192717" THEN "Shea The Hill District"
  WHEN teamwork_id = "186301" THEN "Shea Trilogy"
  WHEN teamwork_id = "180168" THEN "Sub-Zero West"
  WHEN teamwork_id = "190089" THEN "Toll Brothers Arizona"
  WHEN teamwork_id = "155618" THEN "Toll Brothers NorCal"
  WHEN teamwork_id = "163375" THEN "Toll Brothers Santa Clarita"
  WHEN teamwork_id = "101252" THEN "Toll Brothers SoCal"
  WHEN teamwork_id = "179170" THEN "Trumark Homes"
  WHEN teamwork_id = "192553" THEN "Trumark The Collective at Manteca"
  WHEN teamwork_id = "185714" THEN "Van Daele Homes"
  WHEN teamwork_id = "55950" THEN "Woodbridge Pacific Group"
  WHEN teamwork_id = "185051" THEN "Woodbridge Pacific Group Idaho"
  ELSE "Unknown"
END
```

### Google Analytics

AI Bot Traffic: session source medium

`(?i).*gpt.*|.*openai.*|.*neeva.*|.*writesonic.*|.*nimble.*|.*outrider.*|.*perplexity.*|.*google.*bard.*|.*bard.*google.*|.*edgeservices.*|.*gemini.*google.*|.*meta\.ai.*|.*mistral.*|.*copilot.*|.*deepseek.*|.*claude\.ai.*`

GC Organic Traffic Net: medium

`(?i)gc-social|gc-blast|gc-flow|gc-signage|gc-content|gc-popup|gc-press_release|gc-pdf_content`

GC Paid Traffic Net: medium

`(?i)gc-paid|gc-flow|gc-signage|gc-paid_ctv|gc-popup|gc-press_release|gc-pdf_content`

Day of the Week

```bash
CASE
    WHEN WEEKDAY(Date) = 0 THEN "Sunday"
    WHEN WEEKDAY(Date) = 1 THEN "Monday"
    WHEN WEEKDAY(Date) = 2 THEN "Tuesday"
    WHEN WEEKDAY(Date) = 3 THEN "Wednesday"
    WHEN WEEKDAY(Date) = 4 THEN "Thursday"
    WHEN WEEKDAY(Date) = 5 THEN "Friday"
    WHEN WEEKDAY(Date) = 6 THEN "Saturday"
END
```

Time

```bash
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
```

Week Value (text)

`FORMAT_DATETIME('%m/%d/%Y', DATETIME_TRUNC(Date, WEEK))`

Week Date (Date)

`PARSE_DATE("%m/%d/%Y", Week Value)`

'Week' w (M/d/YYYY)

Campaign Phase

```bash
CASE
  WHEN STARTS_WITH(Session Campaign Name, "p1-") THEN "Phase 1"
  WHEN STARTS_WITH(Session Campaign Name, "p2-") THEN "Phase 2"
  WHEN STARTS_WITH(Session Campaign Name, "p3-") THEN "Phase 3"
  WHEN STARTS_WITH(Session Campaign Name, "p4-") THEN "Phase 4"
  WHEN STARTS_WITH(Session Campaign Name, "p5-") THEN "Phase 5"
  WHEN STARTS_WITH(Session Campaign Name, "brand") THEN "Brand"
  ELSE "(not set)"
END
```

Content Pillar

```bash
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

### Days Since Posted

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

### GC Fly Tours

```bash
# Day of the Week
CASE
    WHEN mobile THEN "Mobile"
    WHEN tablet THEN "Tablet"
    WHEN desktop THEN "Desktop"
    ELSE "Other"
END
```
