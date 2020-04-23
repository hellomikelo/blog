---
layout: post
title: Pandas Notes
description: 
published: false
categories: 
- datasci
---

## Tips for idiomatic pandas (some are taken from this [article](https://www.datacamp.com/community/tutorials/pandas-idiomatic))
1. Indexing with the help of `loc` and `iloc`, `query()`
2. Method Chaining, with the help of the `pipe()` function as an alternative to nested functions
3. Memory Optimization, which you can achieve through setting data types
4. `groupby` operation, in the naive and Pandas way
5. Visualization of your DataFrames with Matplotlib and Seaborn
6. Do not do `inplace` operations

# Useful commands: 
* Replace specific cell in DataFrame with new value: `df.replace({'column_name':{'orig_val1': 'new_val1', 'orig_val2':'new_val2'}}, inplace=True)`
* Setting data types in a column of DataFrame: `df.assign(new_col=lambda x: pd.to_datetime(x.existing_col))` or `df.assign(new_col=lambda x: pd.Categorical(x.existing_col))`



