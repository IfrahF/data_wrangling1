Tidy Data
================

# Import SAS

``` r
pulse_df = read_sas("data/public_pulse_data.sas7bdat")
```

## Let’s try to pivot!

Pivot Longer:

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

Pivot Wider:

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
