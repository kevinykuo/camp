
[![Travis build
status](https://travis-ci.org/rstudio/forge.svg?branch=master)](https://travis-ci.org/rstudio/forge)[![Coverage
status](https://codecov.io/gh/rstudio/forge/branch/master/graph/badge.svg)](https://codecov.io/github/rstudio/forge?branch=master)[![AppVeyor
build
status](https://ci.appveyor.com/api/projects/status/github/kevinykuo/forge?branch=master&svg=true)](https://ci.appveyor.com/project/kevinykuo/forge)

<!-- README.md is generated from README.Rmd. Please edit that file -->

# forge

**forge** provides a set of helper functions for input checking and
casting. It is intended to be used by package developers to interoperate
with other language runtimes, such as Python and JVM languages.

## Installation

You can install **forge** from CRAN with

``` r
install.packages("forge")
```

You can install the development version from GitHub with

``` r
devtools::install_github("rstudio/forge")
```

## Examples

``` r
library(sparklyr)
sc <- spark_connect(master = "local")

spark_vector <- function(sc, x) {
  v <- forge::cast_double_list(x)
  invoke_new(sc, "org.apache.spark.ml.linalg.DenseVector", v)
}

spark_vector(sc, 1:3)
#> <jobj[14]>
#>   org.apache.spark.ml.linalg.DenseVector
#>   [1.0,2.0,3.0]
```

-----

Please note that the ‘forge’ project is released with a [Contributor
Code of Conduct](.github/CODE_OF_CONDUCT.md). By contributing to this
project, you agree to abide by its terms.
