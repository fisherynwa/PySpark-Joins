# Geographic Data Enrichment Project

## Aims of the Repo

This repository contains a set of PySpark code and configuration necessary to **load, clean, and enrich** country-level data by applying 3 (sequential) joins with region and sub-region lookup tables.
---

## PySpark Command Executed

The core logic of this project is encapsulated in the following PySpark transformation sequence:

```python
df_joined = df_countries.join(df_regions, df_countries.region_id == df_regions.id, "left").\
  select("country_id", "country", "region", "population", "area_km2", "sub_region_id").\
    join(df_sub_regions, df_countries.sub_region_id == df_sub_regions.id, "left").\
      select("country_id", "country", "region", "sub_region", "population", "area_km2")

```

## Resources and Acknowledgments

Compute Platform: Databricks Community Edition (used for free server access).

Source Data: Provided via a Udemy data engineering course (Country, Region, Sub-Region data).

