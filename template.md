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

### Look at read_csv options

col names and skipping rows

``` r
litters_df = 
  read_csv(
    file = "data/FAS_litters.csv",
    #skip = 2
  )
```

    ## Rows: 49 Columns: 8
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (4): Group, Litter Number, GD0 weight, GD18 weight
    ## dbl (4): GD of Birth, Pups born alive, Pups dead @ birth, Pups survive
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

Missing data and data that interupts data type

``` r
litters_df = 
  read_csv(
    file = "data/FAS_litters.csv",
    na = c("NA", "", ".")
  )
```

    ## Rows: 49 Columns: 8
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (2): Group, Litter Number
    ## dbl (6): GD0 weight, GD18 weight, GD of Birth, Pups born alive, Pups dead @ ...
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
litters_df = janitor::clean_names(litters_df)

gd0_weight = pull(litters_df, gd0_weight)
mean(gd0_weight, na.rm = TRUE)
```

    ## [1] 24.37941

What if we want to code ‘group’ as a factor variable?

``` r
litters_df = 
  read_csv(
    file = "data/FAS_litters.csv",
    na = c("NA", "", "."),
    col_types = cols(
      Group = col_factor()
    )
  )
```

### Import an excel file

Import MLB 2011 summary data

``` r
mlb_df = read_excel("data/mlb11.xlsx", sheet = "mlb11")
```

### Import SAS data

``` r
pulse_df = read_sas("data/public_pulse_data.sas7bdat")
```

## Never use read.csv()

``` r
# litters_df = read.csv("data/FAS_litters.csv")
```

read in without tibble reminders

## Never use \$ to pull out variables

Do not take variables out from a data frame.
