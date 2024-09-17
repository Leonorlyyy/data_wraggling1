Data Import
================

This document will show how to import data.

### Absolute path

Get current working directory using getwd()  
Disadvantages: 1. too complex. 2. Only work in your own computer \###
Relative path \### Import the FAS litters CSV

``` r
litters_df = read_csv("data/FAS_litters.csv")
```

    ## Rows: 49 Columns: 8
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (4): Group, Litter Number, GD0 weight, GD18 weight
    ## dbl (4): GD of Birth, Pups born alive, Pups dead @ birth, Pups survive
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
litters_df = janitor::clean_names(litters_df)


#Lowercases all column names: It converts all column names to lowercase for uniformity.
#Replaces spaces and special characters: Spaces and non-alphanumeric characters (e.g., !, @, #) are replaced with underscores (_).
#Removes leading and trailing whitespace: Any leading or trailing whitespace in column names is removed.
#Ensures names are unique: If there are duplicate column names, it appends a numeric suffix to ensure that each column has a unique name.'''

#head(litters_df)
#tail(litters_df)
```

``` r
View(litters_df)
```

``` r
# relative path
pups_df = read_csv("data/FAS_pups.csv")
pups_df = janitor::clean_names(pups_df)

# Absolute path
pups_df = read_csv("/Users/leyangrui/Desktop/Columbia/Data Science/data_wraggling1/data/FAS_pups.csv")
# --> very fragile, does not work if you move files around
```
