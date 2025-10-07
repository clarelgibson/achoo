# Achoo!
Clare Gibson
2025-06-14

- [Question](#question)
- [Introduction](#introduction)
  - [Packages](#packages)
  - [Data](#data)

# Question

Can Apple Health data help me predict how many times I will sneeze in a
day?

# Introduction

I am a chronic sneezer. Some days I can sneeze all day and all night
long. The sneeze seems to be my body’s default reaction to any kind of
respiratory irritant. I have been diagnosed as having allergies to dust,
grass pollen and cat hair, so my allergic sneezing happens all year
round. On top of that, whenever I get any kind of respiratory virus
(cold, flu, Covid), sneezing is my number one symptom.

Since 1 May 2025 I have been keeping count of the number of times I
sneeze per day. I started doing this primarily to track which days were
my particularly bad “attack” days, but because I also wear an Apple
Watch, I wondered if I might be able to discover any patterns within my
health data that might help to predict my sneeze count. It’s also an
opportunity for me to practise some data science.

## Packages

The code chunk below loads all of the packages needed for this analysis.

``` r
# Load packages
library(here)
library(tidyverse)
library(janitor)
library(googlesheets4)
```

## Data

The data for this analysis is located in [Google
Drive](https://docs.google.com/spreadsheets/d/1pU1wmIuUt1oS-5W6xpchRRMMRrHrKT8KYfvK1saLri0/edit?usp=sharing).

``` r
# Read data into a dataframe
sneezes_raw <- read_sheet(
  ss = "https://docs.google.com/spreadsheets/d/1pU1wmIuUt1oS-5W6xpchRRMMRrHrKT8KYfvK1saLri0/edit?gid=0#gid=0",
  sheet = "data"
)
```

``` r
# Preview the data
glimpse(sneezes_raw)
```

    Rows: 44
    Columns: 9
    $ date    <dttm> 2025-05-01, 2025-05-02, 2025-05-03, 2025-05-04, 2025-05-05, 2…
    $ ae      <dbl> 553, 510, 471, 574, 420, 439, 469, 457, 505, 409, 406, 476, 79…
    $ re      <dbl> 1459, 1446, 1445, 1431, 1416, 1419, 1405, 1421, 1427, 1462, 14…
    $ steps   <dbl> 12795, 13747, 11776, 13566, 9914, 11389, 11252, 9199, 9655, 89…
    $ em      <dbl> 85, 53, 51, 92, 71, 76, 77, 51, 65, 43, 20, 66, 118, 118, 87, …
    $ aeem    <dbl> 6.505882, 9.622642, 9.235294, 6.239130, 5.915493, 5.776316, 6.…
    $ rhr     <dbl> 67, 69, 64, 63, 60, 68, 66, 67, 69, 64, 67, 68, 74, 67, 70, 67…
    $ wt      <dbl> 36.89, 36.80, 36.60, 36.85, 36.99, 37.03, 36.92, 36.74, 36.80,…
    $ sneezes <dbl> 8, 9, 6, 3, 5, 9, 5, 3, 5, 10, 7, 5, 12, 5, 1, 4, 7, 6, 4, 4, …
