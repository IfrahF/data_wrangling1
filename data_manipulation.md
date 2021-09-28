Simple document
================
Ifrah
2021-09-16

# Import Data

I want to import ‘FAS\_litters.csv’.

``` r
litters_df = read.csv("data/FAS_litters.csv")
```

``` r
names(litters_df)
```

    ## [1] "Group"             "Litter.Number"     "GD0.weight"       
    ## [4] "GD18.weight"       "GD.of.Birth"       "Pups.born.alive"  
    ## [7] "Pups.dead...birth" "Pups.survive"

``` r
litters_df = janitor::clean_names(litters_df)
```

# Displaying 20 rows from the start and 10 from the end in litters\_df

``` r
head(litters_df, 20)
```

    ##    group   litter_number gd0_weight gd18_weight gd_of_birth pups_born_alive
    ## 1   Con7             #85       19.7        34.7          20               3
    ## 2   Con7       #1/2/95/2       27.0        42.0          19               8
    ## 3   Con7   #5/5/3/83/3-3       26.0        41.4          19               6
    ## 4   Con7     #5/4/2/95/2       28.5        44.1          19               5
    ## 5   Con7     #4/2/95/3-3         NA          NA          20               6
    ## 6   Con7     #2/2/95/3-2         NA          NA          20               6
    ## 7   Con7 #1/5/3/83/3-3/2         NA          NA          20               9
    ## 8   Con8       #3/83/3-3         NA          NA          20               9
    ## 9   Con8         #2/95/3         NA          NA          20               8
    ## 10  Con8     #3/5/2/2/95       28.5          NA          20               8
    ## 11  Con8     #5/4/3/83/3       28.0          NA          19               9
    ## 12  Con8   #1/6/2/2/95-2         NA          NA          20               7
    ## 13  Con8 #3/5/3/83/3-3-2         NA          NA          20               8
    ## 14  Con8       #2/2/95/2         NA          NA          19               5
    ## 15  Con8   #3/6/2/2/95-3         NA          NA          20               7
    ## 16  Mod7             #59       17.0        33.4          19               8
    ## 17  Mod7            #103       21.4        42.1          19               9
    ## 18  Mod7       #1/82/3-2         NA          NA          19               6
    ## 19  Mod7       #3/83/3-2         NA          NA          19               8
    ## 20  Mod7       #2/95/2-2         NA          NA          20               7
    ##    pups_dead_birth pups_survive
    ## 1                4            3
    ## 2                0            7
    ## 3                0            5
    ## 4                1            4
    ## 5                0            6
    ## 6                0            4
    ## 7                0            9
    ## 8                1            8
    ## 9                0            8
    ## 10               0            8
    ## 11               0            8
    ## 12               0            6
    ## 13               0            8
    ## 14               0            4
    ## 15               0            7
    ## 16               0            5
    ## 17               1            9
    ## 18               0            6
    ## 19               0            8
    ## 20               0            7

``` r
tail(litters_df, 10)
```

    ##    group litter_number gd0_weight gd18_weight gd_of_birth pups_born_alive
    ## 40  Mod8    #7/110/3-2       27.5        46.0          19               8
    ## 41  Mod8       #2/95/2       28.5        44.5          20               9
    ## 42  Mod8         #82/4       33.4        52.7          20               8
    ## 43  Low8           #53       21.8        37.2          20               8
    ## 44  Low8           #79       25.4        43.8          19               8
    ## 45  Low8          #100       20.0        39.2          20               8
    ## 46  Low8         #4/84       21.8        35.2          20               4
    ## 47  Low8          #108       25.6        47.5          20               8
    ## 48  Low8           #99       23.5        39.0          20               6
    ## 49  Low8          #110       25.5        42.7          20               7
    ##    pups_dead_birth pups_survive
    ## 40               1            8
    ## 41               0            9
    ## 42               0            6
    ## 43               1            7
    ## 44               0            7
    ## 45               0            7
    ## 46               0            4
    ## 47               0            7
    ## 48               0            5
    ## 49               0            6

``` r
skimr::skim(litters_df)
```

|                                                  |             |
|:-------------------------------------------------|:------------|
| Name                                             | litters\_df |
| Number of rows                                   | 49          |
| Number of columns                                | 8           |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_   |             |
| Column type frequency:                           |             |
| character                                        | 2           |
| numeric                                          | 6           |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |             |
| Group variables                                  | None        |

Data summary

**Variable type: character**

| skim\_variable | n\_missing | complete\_rate | min | max | empty | n\_unique | whitespace |
|:---------------|-----------:|---------------:|----:|----:|------:|----------:|-----------:|
| group          |          0 |              1 |   4 |   4 |     0 |         6 |          0 |
| litter\_number |          0 |              1 |   3 |  15 |     0 |        49 |          0 |

**Variable type: numeric**

| skim\_variable    | n\_missing | complete\_rate |  mean |   sd |   p0 |   p25 |   p50 |   p75 | p100 | hist  |
|:------------------|-----------:|---------------:|------:|-----:|-----:|------:|------:|------:|-----:|:------|
| gd0\_weight       |         15 |           0.69 | 24.38 | 3.28 | 17.0 | 22.30 | 24.10 | 26.67 | 33.4 | ▃▇▇▆▁ |
| gd18\_weight      |         17 |           0.65 | 41.52 | 4.05 | 33.4 | 38.88 | 42.25 | 43.80 | 52.7 | ▃▃▇▂▁ |
| gd\_of\_birth     |          0 |           1.00 | 19.65 | 0.48 | 19.0 | 19.00 | 20.00 | 20.00 | 20.0 | ▅▁▁▁▇ |
| pups\_born\_alive |          0 |           1.00 |  7.35 | 1.76 |  3.0 |  6.00 |  8.00 |  8.00 | 11.0 | ▁▃▂▇▁ |
| pups\_dead\_birth |          0 |           1.00 |  0.33 | 0.75 |  0.0 |  0.00 |  0.00 |  0.00 |  4.0 | ▇▂▁▁▁ |
| pups\_survive     |          0 |           1.00 |  6.41 | 2.05 |  1.0 |  5.00 |  7.00 |  8.00 |  9.0 | ▁▃▂▇▇ |

## Arguments in read\_csv

``` r
litters_df =
  read_csv(
    "data/FAS_litters.csv",
    skip = 5,
    col_names = FALSE,
    na = "Low8"
  )
```

    ## Rows: 45 Columns: 8

    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (4): X1, X2, X3, X4
    ## dbl (4): X5, X6, X7, X8

    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
litters_df = read_csv(file = "./data/FAS_litters.csv",
  col_types = cols(
    Group = col_character(),
    `Litter Number` = col_character(),
    `GD0 weight` = col_double(),
    `GD18 weight` = col_double(),
    `GD of Birth` = col_integer(),
    `Pups born alive` = col_integer(),
    `Pups dead @ birth` = col_integer(),
    `Pups survive` = col_integer()
  )
)
tail(litters_df)
```

    ## # A tibble: 6 × 8
    ##   Group `Litter Number` `GD0 weight` `GD18 weight` `GD of Birth`
    ##   <chr> <chr>                  <dbl>         <dbl>         <int>
    ## 1 Low8  #79                     25.4          43.8            19
    ## 2 Low8  #100                    20            39.2            20
    ## 3 Low8  #4/84                   21.8          35.2            20
    ## 4 Low8  #108                    25.6          47.5            20
    ## 5 Low8  #99                     23.5          39              20
    ## 6 Low8  #110                    25.5          42.7            20
    ## # … with 3 more variables: Pups born alive <int>, Pups dead @ birth <int>,
    ## #   Pups survive <int>

## Reading MLB data xlsx file.

``` r
mlb11_df = read_excel("data/mlb11.xlsx")
```

## LotR words file.

``` r
fellow_df = read_excel("data/LotR_Words.xlsx", range = "B3:D6")
```

## Read SAS File

Tried reading SAS file but got errors.

``` r
pulse_df = read_sas("data/public_pulse_data.sas7bdat")
```

## why to never use read.csv instead of read\_csv

read.csv will read everything as a dataframe. read\_csv will read things
as a tibble.

``` r
litters_df_base = read.csv("data/FAS_litters.csv")
```

## How do I export data?

``` r
write_csv(fellow_df, "data/fellowship_words.csv")
```

``` r
litters_data = read_csv("./data/FAS_litters.csv",
  col_types = "ccddiiii")
litters_data = janitor::clean_names(litters_data)

pups_data = read_csv("./data/FAS_pups.csv",
  col_types = "ciiiii")
pups_data = janitor::clean_names(pups_data)
```

# Select Function

``` r
select(litters_data, group, litter_number)
```

    ## # A tibble: 49 × 2
    ##    group litter_number  
    ##    <chr> <chr>          
    ##  1 Con7  #85            
    ##  2 Con7  #1/2/95/2      
    ##  3 Con7  #5/5/3/83/3-3  
    ##  4 Con7  #5/4/2/95/2    
    ##  5 Con7  #4/2/95/3-3    
    ##  6 Con7  #2/2/95/3-2    
    ##  7 Con7  #1/5/3/83/3-3/2
    ##  8 Con8  #3/83/3-3      
    ##  9 Con8  #2/95/3        
    ## 10 Con8  #3/5/2/2/95    
    ## # … with 39 more rows

``` r
select(litters_data, group, gd0_weight, gd18_weight)
```

    ## # A tibble: 49 × 3
    ##    group gd0_weight gd18_weight
    ##    <chr>      <dbl>       <dbl>
    ##  1 Con7        19.7        34.7
    ##  2 Con7        27          42  
    ##  3 Con7        26          41.4
    ##  4 Con7        28.5        44.1
    ##  5 Con7        NA          NA  
    ##  6 Con7        NA          NA  
    ##  7 Con7        NA          NA  
    ##  8 Con8        NA          NA  
    ##  9 Con8        NA          NA  
    ## 10 Con8        28.5        NA  
    ## # … with 39 more rows

``` r
select(pups_data, litter_number, sex, pd_ears)
```

    ## # A tibble: 313 × 3
    ##    litter_number   sex pd_ears
    ##    <chr>         <int>   <int>
    ##  1 #85               1       4
    ##  2 #85               1       4
    ##  3 #1/2/95/2         1       5
    ##  4 #1/2/95/2         1       5
    ##  5 #5/5/3/83/3-3     1       5
    ##  6 #5/5/3/83/3-3     1       5
    ##  7 #5/4/2/95/2       1      NA
    ##  8 #4/2/95/3-3       1       4
    ##  9 #4/2/95/3-3       1       4
    ## 10 #2/2/95/3-2       1       4
    ## # … with 303 more rows

``` r
relocate(litters_data, litter_number, pups_survive)
```

    ## # A tibble: 49 × 8
    ##    litter_number   pups_survive group gd0_weight gd18_weight gd_of_birth
    ##    <chr>                  <int> <chr>      <dbl>       <dbl>       <int>
    ##  1 #85                        3 Con7        19.7        34.7          20
    ##  2 #1/2/95/2                  7 Con7        27          42            19
    ##  3 #5/5/3/83/3-3              5 Con7        26          41.4          19
    ##  4 #5/4/2/95/2                4 Con7        28.5        44.1          19
    ##  5 #4/2/95/3-3                6 Con7        NA          NA            20
    ##  6 #2/2/95/3-2                4 Con7        NA          NA            20
    ##  7 #1/5/3/83/3-3/2            9 Con7        NA          NA            20
    ##  8 #3/83/3-3                  8 Con8        NA          NA            20
    ##  9 #2/95/3                    8 Con8        NA          NA            20
    ## 10 #3/5/2/2/95                8 Con8        28.5        NA            20
    ## # … with 39 more rows, and 2 more variables: pups_born_alive <int>,
    ## #   pups_dead_birth <int>

``` r
rename(litters_data, GROUP = group, LiTtEr_NuMbEr = litter_number)
```

    ## # A tibble: 49 × 8
    ##    GROUP LiTtEr_NuMbEr   gd0_weight gd18_weight gd_of_birth pups_born_alive
    ##    <chr> <chr>                <dbl>       <dbl>       <int>           <int>
    ##  1 Con7  #85                   19.7        34.7          20               3
    ##  2 Con7  #1/2/95/2             27          42            19               8
    ##  3 Con7  #5/5/3/83/3-3         26          41.4          19               6
    ##  4 Con7  #5/4/2/95/2           28.5        44.1          19               5
    ##  5 Con7  #4/2/95/3-3           NA          NA            20               6
    ##  6 Con7  #2/2/95/3-2           NA          NA            20               6
    ##  7 Con7  #1/5/3/83/3-3/2       NA          NA            20               9
    ##  8 Con8  #3/83/3-3             NA          NA            20               9
    ##  9 Con8  #2/95/3               NA          NA            20               8
    ## 10 Con8  #3/5/2/2/95           28.5        NA            20               8
    ## # … with 39 more rows, and 2 more variables: pups_dead_birth <int>,
    ## #   pups_survive <int>

# Filter

``` r
filter(litters_data, gd_of_birth == 20)
```

    ## # A tibble: 32 × 8
    ##    group litter_number   gd0_weight gd18_weight gd_of_birth pups_born_alive
    ##    <chr> <chr>                <dbl>       <dbl>       <int>           <int>
    ##  1 Con7  #85                   19.7        34.7          20               3
    ##  2 Con7  #4/2/95/3-3           NA          NA            20               6
    ##  3 Con7  #2/2/95/3-2           NA          NA            20               6
    ##  4 Con7  #1/5/3/83/3-3/2       NA          NA            20               9
    ##  5 Con8  #3/83/3-3             NA          NA            20               9
    ##  6 Con8  #2/95/3               NA          NA            20               8
    ##  7 Con8  #3/5/2/2/95           28.5        NA            20               8
    ##  8 Con8  #1/6/2/2/95-2         NA          NA            20               7
    ##  9 Con8  #3/5/3/83/3-3-2       NA          NA            20               8
    ## 10 Con8  #3/6/2/2/95-3         NA          NA            20               7
    ## # … with 22 more rows, and 2 more variables: pups_dead_birth <int>,
    ## #   pups_survive <int>

``` r
filter(litters_data, gd0_weight < 23)
```

    ## # A tibble: 12 × 8
    ##    group litter_number gd0_weight gd18_weight gd_of_birth pups_born_alive
    ##    <chr> <chr>              <dbl>       <dbl>       <int>           <int>
    ##  1 Con7  #85                 19.7        34.7          20               3
    ##  2 Mod7  #59                 17          33.4          19               8
    ##  3 Mod7  #103                21.4        42.1          19               9
    ##  4 Mod7  #5/3/83/5-2         22.6        37            19               5
    ##  5 Mod7  #106                21.7        37.8          20               5
    ##  6 Mod7  #62                 19.5        35.9          19               7
    ##  7 Low7  #107                22.6        42.4          20               9
    ##  8 Low7  #85/2               22.2        38.5          20               8
    ##  9 Low7  #102                22.6        43.3          20              11
    ## 10 Low8  #53                 21.8        37.2          20               8
    ## 11 Low8  #100                20          39.2          20               8
    ## 12 Low8  #4/84               21.8        35.2          20               4
    ## # … with 2 more variables: pups_dead_birth <int>, pups_survive <int>

``` r
filter(litters_data, pups_survive != 4)
```

    ## # A tibble: 44 × 8
    ##    group litter_number   gd0_weight gd18_weight gd_of_birth pups_born_alive
    ##    <chr> <chr>                <dbl>       <dbl>       <int>           <int>
    ##  1 Con7  #85                   19.7        34.7          20               3
    ##  2 Con7  #1/2/95/2             27          42            19               8
    ##  3 Con7  #5/5/3/83/3-3         26          41.4          19               6
    ##  4 Con7  #4/2/95/3-3           NA          NA            20               6
    ##  5 Con7  #1/5/3/83/3-3/2       NA          NA            20               9
    ##  6 Con8  #3/83/3-3             NA          NA            20               9
    ##  7 Con8  #2/95/3               NA          NA            20               8
    ##  8 Con8  #3/5/2/2/95           28.5        NA            20               8
    ##  9 Con8  #5/4/3/83/3           28          NA            19               9
    ## 10 Con8  #1/6/2/2/95-2         NA          NA            20               7
    ## # … with 34 more rows, and 2 more variables: pups_dead_birth <int>,
    ## #   pups_survive <int>

``` r
filter(litters_data, !(group == "Con7"))
```

    ## # A tibble: 42 × 8
    ##    group litter_number   gd0_weight gd18_weight gd_of_birth pups_born_alive
    ##    <chr> <chr>                <dbl>       <dbl>       <int>           <int>
    ##  1 Con8  #3/83/3-3             NA          NA            20               9
    ##  2 Con8  #2/95/3               NA          NA            20               8
    ##  3 Con8  #3/5/2/2/95           28.5        NA            20               8
    ##  4 Con8  #5/4/3/83/3           28          NA            19               9
    ##  5 Con8  #1/6/2/2/95-2         NA          NA            20               7
    ##  6 Con8  #3/5/3/83/3-3-2       NA          NA            20               8
    ##  7 Con8  #2/2/95/2             NA          NA            19               5
    ##  8 Con8  #3/6/2/2/95-3         NA          NA            20               7
    ##  9 Mod7  #59                   17          33.4          19               8
    ## 10 Mod7  #103                  21.4        42.1          19               9
    ## # … with 32 more rows, and 2 more variables: pups_dead_birth <int>,
    ## #   pups_survive <int>

``` r
filter(litters_data, group %in% c("Con7", "Con8"))
```

    ## # A tibble: 15 × 8
    ##    group litter_number   gd0_weight gd18_weight gd_of_birth pups_born_alive
    ##    <chr> <chr>                <dbl>       <dbl>       <int>           <int>
    ##  1 Con7  #85                   19.7        34.7          20               3
    ##  2 Con7  #1/2/95/2             27          42            19               8
    ##  3 Con7  #5/5/3/83/3-3         26          41.4          19               6
    ##  4 Con7  #5/4/2/95/2           28.5        44.1          19               5
    ##  5 Con7  #4/2/95/3-3           NA          NA            20               6
    ##  6 Con7  #2/2/95/3-2           NA          NA            20               6
    ##  7 Con7  #1/5/3/83/3-3/2       NA          NA            20               9
    ##  8 Con8  #3/83/3-3             NA          NA            20               9
    ##  9 Con8  #2/95/3               NA          NA            20               8
    ## 10 Con8  #3/5/2/2/95           28.5        NA            20               8
    ## 11 Con8  #5/4/3/83/3           28          NA            19               9
    ## 12 Con8  #1/6/2/2/95-2         NA          NA            20               7
    ## 13 Con8  #3/5/3/83/3-3-2       NA          NA            20               8
    ## 14 Con8  #2/2/95/2             NA          NA            19               5
    ## 15 Con8  #3/6/2/2/95-3         NA          NA            20               7
    ## # … with 2 more variables: pups_dead_birth <int>, pups_survive <int>

``` r
filter(litters_data, group == "Con7", gd_of_birth == 20)
```

    ## # A tibble: 4 × 8
    ##   group litter_number   gd0_weight gd18_weight gd_of_birth pups_born_alive
    ##   <chr> <chr>                <dbl>       <dbl>       <int>           <int>
    ## 1 Con7  #85                   19.7        34.7          20               3
    ## 2 Con7  #4/2/95/3-3           NA          NA            20               6
    ## 3 Con7  #2/2/95/3-2           NA          NA            20               6
    ## 4 Con7  #1/5/3/83/3-3/2       NA          NA            20               9
    ## # … with 2 more variables: pups_dead_birth <int>, pups_survive <int>

# Mutate

Let’s add or change things:

``` r
mutate(
  litters_data, 
  weight_change = gd18_weight - gd0_weight,
  group = str_to_lower(group)
  )
```

    ## # A tibble: 49 × 9
    ##    group litter_number   gd0_weight gd18_weight gd_of_birth pups_born_alive
    ##    <chr> <chr>                <dbl>       <dbl>       <int>           <int>
    ##  1 con7  #85                   19.7        34.7          20               3
    ##  2 con7  #1/2/95/2             27          42            19               8
    ##  3 con7  #5/5/3/83/3-3         26          41.4          19               6
    ##  4 con7  #5/4/2/95/2           28.5        44.1          19               5
    ##  5 con7  #4/2/95/3-3           NA          NA            20               6
    ##  6 con7  #2/2/95/3-2           NA          NA            20               6
    ##  7 con7  #1/5/3/83/3-3/2       NA          NA            20               9
    ##  8 con8  #3/83/3-3             NA          NA            20               9
    ##  9 con8  #2/95/3               NA          NA            20               8
    ## 10 con8  #3/5/2/2/95           28.5        NA            20               8
    ## # … with 39 more rows, and 3 more variables: pups_dead_birth <int>,
    ## #   pups_survive <int>, weight_change <dbl>

## Arrange

``` r
arrange(litters_data, desc(gd0_weight))
```

    ## # A tibble: 49 × 8
    ##    group litter_number gd0_weight gd18_weight gd_of_birth pups_born_alive
    ##    <chr> <chr>              <dbl>       <dbl>       <int>           <int>
    ##  1 Mod8  #82/4               33.4        52.7          20               8
    ##  2 Con7  #5/4/2/95/2         28.5        44.1          19               5
    ##  3 Con8  #3/5/2/2/95         28.5        NA            20               8
    ##  4 Mod8  #2/95/2             28.5        44.5          20               9
    ##  5 Con8  #5/4/3/83/3         28          NA            19               9
    ##  6 Mod7  #3/82/3-2           28          45.9          20               5
    ##  7 Mod8  #7/110/3-2          27.5        46            19               8
    ##  8 Con7  #1/2/95/2           27          42            19               8
    ##  9 Mod8  #7/82-3-2           26.9        43.2          20               7
    ## 10 Con7  #5/5/3/83/3-3       26          41.4          19               6
    ## # … with 39 more rows, and 2 more variables: pups_dead_birth <int>,
    ## #   pups_survive <int>

``` r
arrange(litters_data, gd_of_birth, gd0_weight)
```

    ## # A tibble: 49 × 8
    ##    group litter_number gd0_weight gd18_weight gd_of_birth pups_born_alive
    ##    <chr> <chr>              <dbl>       <dbl>       <int>           <int>
    ##  1 Mod7  #59                 17          33.4          19               8
    ##  2 Mod7  #62                 19.5        35.9          19               7
    ##  3 Mod7  #103                21.4        42.1          19               9
    ##  4 Mod7  #5/3/83/5-2         22.6        37            19               5
    ##  5 Mod7  #4/2/95/2           23.5        NA            19               9
    ##  6 Low7  #112                23.9        40.5          19               6
    ##  7 Mod7  #94/2               24.4        42.9          19               7
    ##  8 Low8  #79                 25.4        43.8          19               8
    ##  9 Con7  #5/5/3/83/3-3       26          41.4          19               6
    ## 10 Con7  #1/2/95/2           27          42            19               8
    ## # … with 39 more rows, and 2 more variables: pups_dead_birth <int>,
    ## #   pups_survive <int>
