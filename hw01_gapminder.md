STAT 545 Assignment 1
================
Lucy Bellemare
September 11, 2018

``` r
library(gapminder)
library(tidyr)
```

Using the Gapminder dataset, let's explore a little! First let's consider how average gdp per capita has changed across continents from 1952 to 2007:

``` r
test <- aggregate(gapminder$gdpPercap, by=list(gapminder$continent, gapminder$year), FUN=mean)
colnames(test) <- c("Continent", "Year", "GDPPerCap")
test2 <- test %>% spread(Continent, GDPPerCap)
test2
```

    ##    Year   Africa  Americas      Asia    Europe  Oceania
    ## 1  1952 1252.572  4079.063  5195.484  5661.057 10298.09
    ## 2  1957 1385.236  4616.044  5787.733  6963.013 11598.52
    ## 3  1962 1598.079  4901.542  5729.370  8365.487 12696.45
    ## 4  1967 2050.364  5668.253  5971.173 10143.824 14495.02
    ## 5  1972 2339.616  6491.334  8187.469 12479.575 16417.33
    ## 6  1977 2585.939  7352.007  7791.314 14283.979 17283.96
    ## 7  1982 2481.593  7506.737  7434.135 15617.897 18554.71
    ## 8  1987 2282.669  7793.400  7608.227 17214.311 20448.04
    ## 9  1992 2281.810  8044.934  8639.690 17061.568 20894.05
    ## 10 1997 2378.760  8889.301  9834.093 19076.782 24024.18
    ## 11 2002 2599.385  9287.677 10174.090 21711.732 26938.78
    ## 12 2007 3089.033 11003.032 12473.027 25054.482 29810.19

From this we can see that the average GDP per capita for each continent has steadily increased from 1952 to 2007. Let's see if the same trend can be observed in average life expectancy, over the same time period:

``` r
test3 <- aggregate(gapminder$lifeExp, by=list(gapminder$continent, gapminder$year), FUN=mean)
colnames(test3) <- c("Continent", "Year", "LifeExp")
test4 <- test3 %>% spread(Continent, LifeExp)
test4
```

    ##    Year   Africa Americas     Asia   Europe Oceania
    ## 1  1952 39.13550 53.27984 46.31439 64.40850 69.2550
    ## 2  1957 41.26635 55.96028 49.31854 66.70307 70.2950
    ## 3  1962 43.31944 58.39876 51.56322 68.53923 71.0850
    ## 4  1967 45.33454 60.41092 54.66364 69.73760 71.3100
    ## 5  1972 47.45094 62.39492 57.31927 70.77503 71.9100
    ## 6  1977 49.58042 64.39156 59.61056 71.93777 72.8550
    ## 7  1982 51.59287 66.22884 62.61794 72.80640 74.2900
    ## 8  1987 53.34479 68.09072 64.85118 73.64217 75.3200
    ## 9  1992 53.62958 69.56836 66.53721 74.44010 76.9450
    ## 10 1997 53.59827 71.15048 68.02052 75.50517 78.1900
    ## 11 2002 53.32523 72.42204 69.23388 76.70060 79.7400
    ## 12 2007 54.80604 73.60812 70.72848 77.64860 80.7195

Yes, the same trend is observed when considering average life expectancy for each continent.
