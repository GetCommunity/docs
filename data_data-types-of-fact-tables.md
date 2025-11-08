# Data Fact Tables

- [The Three Types of Fact Tables](https://www.holistics.io/blog/the-three-types-of-fact-tables/)
- [Types of Fact Tables in a Data Warehouse by Chandru Gurumoorthi](https://medium.com/@changuru2023/types-of-fact-tables-data-warehouse-cec3cfaa2efe)

## Transaction Fact Tables

- To capture the occurrence of a thing, record a transaction in your data warehouse each time it happens.
- Each row in a transactional fact table represents a single event or transaction.
- For example: a sales transaction, a website visit, or a customer support interaction.
- The grain (or level of detail) is typically one row per transaction.

## Periodic Snapshot Tables

- These are a logical extension to the [Transactional Fact Tables](#transaction-fact-tables) and are used to capture the state of a process at regular intervals.
- For example: a daily snapshot of financial metrics, a weekly summary of accounts receivable, a monthly tally of inventory numbers
- The ‘grain’ or ‘level of resolution’ is the period.
- Note that if no transactions occur during a certain period, a new row must be inserted into the periodic snapshot table, even if every fact that is saved is a null!

## Accumulating Snapshot Tables

- This measures velocity within the business process.
- It tracks the progress of a process that has a defined beginning and end, such as an order fulfillment or a customer support ticket.
- The table is updated as the process moves through its various stages.
- For example: an order fulfillment table might have fields for order placed date, order shipped date, and order delivered date.
- The grain is one row per process instance (e.g., one row per order).
- This type of fact table is useful for analyzing the efficiency and duration of business processes.
