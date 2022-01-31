# Earned-Doctorates

The details of the codeset and plots are included in the attached Microsoft Word Document (.docx) file in this repository. 
You need to view the file in "Read Mode" to see the contents properly after downloading the same.

A Brief Introduction
======================


<!-- README.md is generated from README.Rmd. Please edit that file -->

# gghighlight

Highlight geoms in ggplot2.

## Installation

``` r
install.packages("gghighlight")

```

## Example

Suppose we have a data that has so many series that it is hard to
identify them by their colours as the differences are so subtle.

``` r
library(ggplot2)

ggplot(d) +
  geom_line(aes(idx, value, colour = type))
```

![image](https://user-images.githubusercontent.com/26252963/151749522-de23751c-c4ce-4dca-8ed0-954f7d0464b1.png)


With `gghighlight()`, we can highlight the lines whose max values are
larger than 20:

``` r
library(gghighlight)

p <- ggplot(d) +
  geom_line(aes(idx, value, colour = type)) +
  gghighlight(max(value) > 19)
#> label_key: type

p
```

![image](https://user-images.githubusercontent.com/26252963/151749618-0164e0fe-f8ad-4987-8caa-ce373c8b2969.png)

The result is a usual ggplot object, so it is fully customizable. For
example, it can be used with custom themes and facets.

``` r
p + theme_minimal()
```

![image](https://user-images.githubusercontent.com/26252963/151749645-457ffbef-4769-40d2-98b4-a2f5177658c1.png)

``` r
p + theme_minimal() + facet_wrap(~ type)
```

![image](https://user-images.githubusercontent.com/26252963/151749669-d9c56610-49ec-4d6d-bc18-61b89808d615.png)

`gghighlight()` can highlight almost any geoms.

