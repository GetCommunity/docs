# Budget Spend Pacing

## Variables

- `budget` — The effective monthly budget to pace against: `platform_budget` when it exists and is greater than 0, otherwise `budget_net`.
- `days_in_month` — Total number of calendar days in the budget's year/month.
- `day_of_month` — The current day number within the month (1-based).
- `month_to_date_ratio` — Fraction of the month elapsed so far: `day_of_month / days_in_month`.
- `expected_spend_mtd` — The amount that should have been spent by today if spend were perfectly linear across the month: `budget * month_to_date_ratio`.
- `spend_mtd` — Actual amount spent so far this month (month-to-date).
- `actual_budget_ratio` — Fraction of the total budget spent so far: `spend_mtd / budget`.
- `pacing_ratio` — Actual spend relative to expected spend at this point in the month: `spend_mtd / expected_spend_mtd`. Greater than 1 means overspending pace; less than 1 means underspending pace.
- `pacing_percent` — `pacing_ratio` expressed as a percentage: `pacing_ratio * 100`.
- `pacing_variance` — Dollar difference between actual and expected spend to date: `spend_mtd - expected_spend_mtd`. Positive means ahead of pace (overspending); negative means behind pace (underspending).
- `projected_month_spend` — Estimated total spend by month end if the current daily pace continues: `spend_mtd / month_to_date_ratio`.
- `projected_variance` — Estimated dollar difference between projected month-end spend and budget: `projected_month_spend - budget`. Positive means projected to exceed budget; negative means projected to come in under budget.

## Algorithm

### Determine the effective budget

```ts
IF platform_budget exists AND platform_budget > 0:
      budget = platform_budget
ELSE:
      budget = budget_net

// LS Formula
IF(Platform Budget > 0, Platform Budget, Budget Net)
```

### Calculate the number of days in the month

```ts
days_in_month = number of calendar days in year/month

// LS Formula
CASE
  WHEN Date IS NULL THEN 0
  ELSE DAY(
    DATETIME_SUB(
      DATETIME_ADD(
        DATETIME_TRUNC(Date, MONTH),
        INTERVAL 1 MONTH
      ),
      INTERVAL 1 DAY
    )
  )
END
```

### Calculate how far through the month we are

```ts
month_to_date_ratio = day_of_month / days_in_month

// LS Formula
IF(IFNULL(days_in_Month, 0) > 0, day_of_month / days_in_month, 0)
```

### Calculate expected spend through today

```ts
expected_spend_mtd = budget * month_to_date_ratio
```

### Calculate actual percentage of budget spent

```ts
actual_budget_ratio = spend_mtd / budget

// LS Formula
IF(IFNULL(budget, 0) > 0, spend_mtd / budget, 0)
```

### Calculate pacing ratio

```ts
pacing_ratio = spend_mtd / expected_spend_mtd
```

### Calculate pacing percentage

```ts
pacing_percent = pacing_ratio * 100
```

### Calculate dollar variance from expected pace

```ts
pacing_variance = spend_mtd - expected_spend_mtd

// LS Formula
IF(IFNULL(expected_spend_mtd, 0) > 0, spend_mtd - expected_spend_mtd, 0)
```

### Estimate end-of-month spend at the current pace

```ts
projected_month_spend = spend_mtd / month_to_date_ratio
```

### Calculate projected budget variance

```ts
projected_variance = projected_month_spend - budget
```
