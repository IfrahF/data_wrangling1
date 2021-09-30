Tidy Data
================

# Import SAS

``` r
pulse_df = read_sas("data/public_pulse_data.sas7bdat")
```

# Let’s try to pivot!

## Pivot Longer:

``` r
pulse_tidy = 
  pulse_df %>%
  pivot_longer(
    BDIScore_BL:BDIScore_12m,
    names_to = "visit",
    names_prefix = "BDIScore_",
    values_to = "bdi"
  ) %>%
  mutate(
    visit = replace(visit, visit == "BL", "00m"),
    visit = factor(visit)
  )
```

## Pivot Wider:

``` r
analysis_df = tibble(
  group = c("treatment", "treatment", "placebo", "placebo"),
  time = c("pre", "post", "pre", "post"),
  group_mean = c(4, 8, 3.5, 4)
)

analysis_df %>%
  pivot_wider(
    names_from = "time",
    values_from = "group_mean"
  ) %>%
  knitr::kable()
```

| group     | pre | post |
|:----------|----:|-----:|
| treatment | 4.0 |    8 |
| placebo   | 3.5 |    4 |

## Bind Rows:

Import LotR Words Spreadsheet

``` r
fellowship_df = 
  read_excel("data/LotR_Words.xlsx", range = "B3:D6") %>%
  mutate(movie = "fellowship_rings")

two_towers_df = 
  read_excel("data/LotR_Words.xlsx", range = "F3:H6") %>%
  mutate(movie = "two_towers")

return_king_df = 
  read_excel("data/LotR_Words.xlsx", range = "J3:L6") %>%
  mutate(movie = "return_king")

lotr_df = 
  bind_rows(fellowship_df, two_towers_df, return_king_df) %>%
  janitor::clean_names() %>%
  pivot_longer(
    female:male,
    names_to = "sex",
    values_to = "words"
  ) %>%
  relocate(movie)
```
