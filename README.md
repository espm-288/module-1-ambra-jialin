# Module 1: Tabular Data

Working with larger-than-RAM data using duckdbfs

**Authors**: Jialin and Ambra  
**Course**: ESPM 288

## Overview

This module explores high-performance workflows for working with tabular data that exceeds available RAM. We use `duckdbfs` to leverage DuckDB's streaming and remote file access capabilities, enabling efficient analysis of large-scale datasets without downloading them locally.

## Case Study: Global Supply Chains

We analyze [EXIOBASE 3.8.1](https://source.coop/youssef-harby/exiobase-3), a global Multi-Regional Input-Output (MRIO) database that tracks economic transactions between sectors and regions, along with their environmental impacts.

### Dataset Specifications

- **Coverage**: 44 countries + 5 rest-of-world regions
- **Timeframe**: 1995–2022
- **Content**: 
  - Economic transactions (Z matrix)
  - Final demand (Y matrix)
  - Environmental stressors (F matrix)
- **Format**: Cloud-optimized Parquet, partitioned by year and matrix type
- **Source**: Hosted on Source Cooperative

## Contents

- `tabular-data.qmd`: Main analysis document with exercises
- `implementation_python.ipynb`: Python implementation of the exercises

## Requirements

```r
install.packages("duckdbfs")
install.packages("dplyr")
```

## Key Learning Objectives

1. **Connect to remote data** without downloading using `open_dataset()`
2. **Efficient filtering** of large datasets before collecting into memory
3. **Query optimization** for cloud-based data analysis
4. **Environmental data analysis** focusing on CO2 emissions by sector

## Exercises

### Exercise 1: Connecting to Remote Data

Learn how to connect to cloud-hosted datasets using S3 paths and configure DuckDB secrets for secure access.

### Exercise 2: Efficient Filtering

Practice filtering large datasets before loading data into memory. Includes a task to find the top 5 sectors in the US by CO2 emissions in 2022.

## Data Access

The EXIOBASE data is accessed via:
```
s3://us-west-2.opendata.source.coop/youssef-harby/exiobase-3/4588235/parquet/
```

## Usage

Open and run the `tabular-data.qmd` file in RStudio or render it using Quarto:

```bash
quarto render tabular-data.qmd
```

## Notes

- The dataset is accessed remotely using S3, so no local download is required
- All filtering operations are performed on the remote data before collecting into R
- DuckDB handles the optimization and streaming of data automatically