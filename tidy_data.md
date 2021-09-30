Tidy Data
================

# Import SAS

``` r
pulse_df = read_sas("data/public_pulse_data.sas7bdat")
```

Let’s try to pivot!

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
