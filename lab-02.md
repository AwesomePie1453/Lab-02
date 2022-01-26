Lab 02 - Plastic waste
================
Alex Connolly
01/26/2022

## Load packages and data

``` r
library(tidyverse) 
```

``` r
plastic_waste <- read.csv("data/plastic-waste.csv")
```

## Exercises

### Exercise 1

``` r
ggplot(data = plastic_waste, aes(x = plastic_waste_per_cap))+geom_histogram(binwidth = .2)
```

    ## Warning: Removed 51 rows containing non-finite values (stat_bin).

![](lab-02_files/figure-gfm/plastic-waste-continent-1.png)<!-- -->

``` r
plastic_waste %>%
  filter(plastic_waste_per_cap>3.5)
```

    ##   code              entity     continent year gdp_per_cap plastic_waste_per_cap
    ## 1  TTO Trinidad and Tobago North America 2010    31260.91                   3.6
    ##   mismanaged_plastic_waste_per_cap mismanaged_plastic_waste coastal_pop
    ## 1                             0.19                    94066     1358433
    ##   total_pop
    ## 1   1341465

Distributions of plastic waste per capita faceted by continent:

``` r
ggplot(data = plastic_waste, aes(x=plastic_waste_per_cap))+geom_histogram()+facet_wrap(~continent)
```

    ## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

    ## Warning: Removed 51 rows containing non-finite values (stat_bin).

![](lab-02_files/figure-gfm/plastic_continent-1.png)<!-- -->

Density plots:

``` r
ggplot(data=plastic_waste, aes(x= plastic_waste_per_cap)) + geom_density()
```

    ## Warning: Removed 51 rows containing non-finite values (stat_density).

![](lab-02_files/figure-gfm/plastic-density-1.png)<!-- -->

Distributions across continents

``` r
ggplot(data=plastic_waste, mapping = aes(x=plastic_waste_per_cap, color = continent))+ geom_density()
```

    ## Warning: Removed 51 rows containing non-finite values (stat_density).

![](lab-02_files/figure-gfm/plastic-distributions-1.png)<!-- -->

Overlapping colors:

``` r
ggplot(data=plastic_waste, mapping = aes(x=plastic_waste_per_cap, color = continent, fill = continent))+ geom_density()
```

    ## Warning: Removed 51 rows containing non-finite values (stat_density).

![](lab-02_files/figure-gfm/plastic-color-1.png)<!-- -->

Changing Transparency Levels:

``` r
ggplot(data=plastic_waste, mapping = aes(x=plastic_waste_per_cap, color= continent, fill=continent)) + geom_density(alpha=.7)
```

    ## Warning: Removed 51 rows containing non-finite values (stat_density).

![](lab-02_files/figure-gfm/plastic-transparency-1.png)<!-- -->

### Exercise 2

``` r
ggplot(data=plastic_waste, mapping = aes(x=plastic_waste_per_cap, color= continent, fill=continent)) +geom_density(alpha=.12)
```

    ## Warning: Removed 51 rows containing non-finite values (stat_density).

![](lab-02_files/figure-gfm/plastic-new-alpha-1.png)<!-- -->

If you try to put the alpha value within the aestethis, the plot
dissapears completely, which i why we use it as a characteristic of a
plotting geom.

Box Plot:

``` r
ggplot(data=plastic_waste, mapping = aes(x=continent, y=plastic_waste_per_cap))+geom_boxplot()
```

    ## Warning: Removed 51 rows containing non-finite values (stat_boxplot).

![](lab-02_files/figure-gfm/plastic-box-1.png)<!-- -->

### Exercise 3

``` r
ggplot(data=plastic_waste, mapping = aes(x=continent, y=plastic_waste_per_cap))+ geom_violin()
```

    ## Warning: Removed 51 rows containing non-finite values (stat_ydensity).

![](lab-02_files/figure-gfm/violin-plots-1.png)<!-- --> This violin plot
shows us more of the shape of the disstribution, whereas the box plots
show us where the majority of the data lies, and outliers.

### Exercise 4

``` r
ggplot(data=plastic_waste, mapping = aes(x=mismanaged_plastic_waste,y=plastic_waste_per_cap))+ geom_point() 
```

    ## Warning: Removed 51 rows containing missing values (geom_point).

![](lab-02_files/figure-gfm/notcolor-1.png)<!-- --> The relationship
would be linear except for two very obvious outliers, making it more
like a left skewed relationship

``` r
ggplot(data=plastic_waste, mapping = aes(x=mismanaged_plastic_waste,color = continent,  y=plastic_waste_per_cap))+ geom_point() 
```

    ## Warning: Removed 51 rows containing missing values (geom_point).

![](lab-02_files/figure-gfm/plastic-wasste-scatter-1.png)<!-- -->

Its seems that the North American countries have higher waste per
capita, with lower mismanged plastic waste, whereas the Asia countries
have low plastic waste per capita but high mismanaged plastic waste.

``` r
ggplot(data=plastic_waste, mapping = aes(x=total_pop,y=plastic_waste_per_cap))+ geom_point() 
```

    ## Warning: Removed 61 rows containing missing values (geom_point).

![](lab-02_files/figure-gfm/totalpop-1.png)<!-- -->

``` r
ggplot(data=plastic_waste, mapping = aes(x=coastal_pop,y=plastic_waste_per_cap))+ geom_point() 
```

    ## Warning: Removed 51 rows containing missing values (geom_point).

![](lab-02_files/figure-gfm/coastal-pop-1.png)<!-- --> It seems to me
that coastal population apears to have a more linear relationship with
palstic waste per capital than total population has. \#\#\# Exercise 5

### Exercise 6

Remove this text, and add your answer for Exercise 6 here.

``` r
# insert code here
```

### Exercise 7

Remove this text, and add your answer for Exercise 7 here.

``` r
# insert code here
```

``` r
# insert code here
```

### Exercise 8

Remove this text, and add your answer for Exercise 8 here.

``` r
# insert code here
```

## Pro-Tips

### Excercise 3

Try this :D

ggplot(data = plastic\_waste, mapping = aes(x = continent, y =
plastic\_waste\_per\_cap)) + geom\_violin()+ geom\_boxplot(width=.3,
fill=“green”) + stat\_summary(fun.y=median, geom=“point”)

### Exercise 5

Helpful
reference:<http://www.sthda.com/english/wiki/ggplot2-themes-and-background-colors-the-3-elements>
