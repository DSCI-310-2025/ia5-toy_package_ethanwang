
<!-- README.md is generated from README.Rmd. Please edit that file -->

# toypackage

<!-- badges: start -->
<!-- badges: end -->

The goal of **toypackage** is to provide simple, helpful tools for
working with strings — starting with a lightweight wrapper around base
R’s `strsplit()`.

## Installation

You can install the development version of `toypackage` from
[GitHub](https://github.com) with:

``` r
# install.packages("devtools")
devtools::install_github("your-username/toypackage")
```

## Example

A common task when working with strings is splitting a comma-separated
string into parts:

``` r
x <- "alfa,bravo,charlie,delta"
strsplit(x, split = ",")
#> [[1]]
#> [1] "alfa"    "bravo"   "charlie" "delta"
```

This returns a **list of length 1** — which is often more than you want.
That’s where `str_split_one()` comes in.

``` r
library(toypackage)

str_split_one(x, pattern = ",")
#> [1] "alfa"    "bravo"   "charlie" "delta"
```

Use str_split_one() when the input is known to be a single string. For
safety, it will error if its input has length greater than one.

str_split_one() is built on stringr::str_split(), so you can use its n
argument and stringr’s general interface for describing the pattern to
be matched.

``` r
str_split_one(x, pattern = ",", n = 2)
#> [1] "alfa"                "bravo,charlie,delta"

y <- "192.168.0.1"
str_split_one(y, pattern = stringr::fixed("."))
#> [1] "192" "168" "0"   "1"
```

## Future Goals

This package might later include: - Pattern matching helpers - String
cleaning tools - More readable versions of base string functions

Stay tuned!
