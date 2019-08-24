---
layout: post
title: Running Index for SQL Queries
---

In my work at a micromobility startup, we have numerous ground assets at any given point of time, each being handled by users and operators. These assets could be either ready for hire, being moved around or is in the workshop.

In tracking the performance of the business, it is natural to ask what is the performance of each/all the assets. Each minute the asset is spent in the workshop is each minute of revenue lost.

### Challenge
In my case, the data is stored in a database as logs, with each record being a touchpoint made on an asset, and a classfication type of touchpoint made. All the assets are written in the same table. Within the constraints of SQL, I had to create a query on the database and link it directly in Tableau, creating a live feed of the assets.

With this, I wanted to answer these questions:
- How long did an asset spend in a specific touchpoint type or a given touchpoint?
- For each asset, how could I string together all its touchpoints?
- What about the entire fleet of assets?

#### Solution
Since the touchpoints are live and continuous, the database index wasn't particularly helpful, and the timestamps and asset ID provided the order of touchpoints for a particular asset. I needed to generate a new index number for each record, from which further manipulation of the data can be done. 

In short, for each asset ID, I needed a running index based on the timestamp. 2 queries from the same dataset is needed, with 1 of queries having an index offset by 1. For example:

```
asset_id | time  | type | index1
2        | 00:00 | A    | 1
2        | 01:01 | B    | 2
2        | 02:03 | A    | 3

asset_id | time  | type | index2
2        | 00:00 | A    | 0
2        | 01:01 | B    | 1
2        | 02:03 | A    | 2
```

With this a join on `asset_id` and `index` will create something like this:

```
asset_id | time1 | type1 | index1 | time2 | type2  | index2
2        | 00:00 | A     | 1      | 01:01 | B      | 1
2        | 01:01 | B     | 2      | 02:03 | A      | 2
```

An existing solution to this is to use the built in `ROW_NUMBER` or `ROWNUMBER` functions in the database. Or a simple subquery like below, where the starting number and intervals can be set accordingly.

```sql
select
        (@row_number:=@row_number + 1) AS num
    from
        (SELECT @row_number:=0) as rn,
        tablename
```




