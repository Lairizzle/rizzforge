---
title: 'Python Modules - Framezip'
date: 2025-07-29T00:00:00-04:00
draft: false
author: Keith Henderson
tags: ['computers', 'programming', 'python', 'pip', 'data']
---

## A Data Challenge
I was having a discussion with someone at work and we were talking about event level data. If you are not familiar with event level data it can look something like this:

| GroupID | EventID | EventName       | Timestamp           | UserID | Details                      |
| ------- | ------- | --------------- | ------------------- | ------ | ---------------------------- |
| G001    | E101    | Login           | 2025-07-30 09:15:23 | U001   | Successful login             |
| G001    | E102    | View Dashboard  | 2025-07-30 09:16:10 | U001   | Loaded user dashboard        |
| G001    | E103    | Download Report | 2025-07-30 09:18:44 | U001   | Report ID: R567              |
| G002    | E201    | Login           | 2025-07-30 10:02:11 | U002   | Failed password (2 attempts) |
| G002    | E202    | Password Reset  | 2025-07-30 10:04:55 | U002   | Sent reset email             |
| G002    | E203    | Login           | 2025-07-30 10:10:32 | U002   | Successful login             |
| G003    | E301    | Add to Cart     | 2025-07-30 11:20:14 | U003   | Item ID: P908                |
| G003    | E302    | Checkout        | 2025-07-30 11:25:00 | U003   | Order ID: O12345             |
| G003    | E303    | Payment Success | 2025-07-30 11:27:10 | U003   | Payment via credit card      |

Data like this can quickly balloon into a massive amount of records very quickly. Let's assume that every interaction has 6 events inside of it and lets imagine you had 6 billion records. What if you could compress that down to 1 billion and represent every interaction as a single record? It sounded like a cool idea, but I still was not sure if it was actually more efficient or not.

## When is this more efficient?
Data Storage:
- This is definitely smaller since repeated fields (GroupID, UserID) are stored once, and columnar/JSON compression can shrink it further.

ETL (processing):
- This would have faster to load/write since there are fewer records (1 per group, not N per event).

Querying sessions or interactions as a whole:
- If most queries pull all events for a group, this structure is optimal.

## When is this less efficient?

- If you need to filter by event attributes often (“count all Login events across all groups”), you’ll have to explode/flatten the arrays in most databases, which can slow queries.

- Some SQL databases handle arrays poorly; it may work best in a document store (MongoDB) or columnar database (Snowflake, BigQuery, ClickHouse) that supports arrays natively.

## What is the best option?
Columnar Warehouses with array support (Snowflake, BigQuery, ClickHouse)

- Store as a table but use ARRAY columns.
- Querying by session is fast, and they can efficiently unnest arrays when needed.

## Is this useful?
I would say possibly. In the case of something like Snowflake, which can utilize array columns, you could bring whatever data you need through framezip and prepare it for Snowflake. When loading it into Snowflake you only need to do something like this:

Push the data processed with framezip to parquet:
```python
packed.to_parquet("sessions.parquet")
```
Load the parquet into Snowflake and define the array columns:
```sql
CREATE OR REPLACE TABLE sessions_raw (
  GroupID STRING,
  EventID ARRAY,
  Value ARRAY
);

COPY INTO sessions_raw
FROM @my_stage/sessions.parquet
FILE_FORMAT = (TYPE = PARQUET);
```
## In the end
In the end it was cool to create and publish a module to PyPi. It always feels great to have a random idea and execute on it. It was a lot of fun and I learned a lot through the entire process and to be honest that is all that really matters.

You can find the module on PyPi [here](https://pypi.org/project/framezip/).

Below is a link to framezip on Github:
{{< github user="lairizzle" repo="framezip" >}}

Cheers,
Keith






