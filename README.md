
<!-- README.md is generated from README.Rmd. Please edit that file -->

# nflreadr

<!-- badges: start -->
<!-- [![CRAN status](https://img.shields.io/cran/v/nflreadr?style=flat-square&logo=R&label=CRAN)](https://CRAN.R-project.org/package=nflreadr)  -->
<!-- [![Codecov test coverage](https://img.shields.io/codecov/c/github/nflverse/nflreadr?label=codecov&style=flat-square&logo=codecov)](https://codecov.io/gh/nflverse/nflreadr?branch=main) -->

[![Dev
status](https://img.shields.io/github/r-package/v/nflverse/nflreadr/master?label=dev&style=flat-square&logo=github)](https://nflreadr.nflverse.com/)
[![Lifecycle:
experimental](https://img.shields.io/badge/lifecycle-experimental-orange.svg?style=flat-square)](https://lifecycle.r-lib.org/articles/stages.html)
[![R build
status](https://img.shields.io/github/workflow/status/nflverse/nflreadr/R-CMD-check?label=R%20check&style=flat-square&logo=github)](https://github.com/nflverse/nflreadr/actions)
[![nflverse
discord](https://img.shields.io/discord/591914197219016707.svg?color=5865F2&label=nflverse%20discord&logo=discord&logoColor=5865F2&style=flat-square)](https://discord.com/invite/5Er2FBnnQa)

<!-- badges: end -->

nflreadr is a low-level package for downloading data from nflverse
repositories.

## Installation

Install the development version from GitHub with:

``` r
install.packages("nflreadr", repos = "https://nflverse.r-universe.dev")

# or use remotes/devtools
# install.packages("remotes")
remotes::install_github("nflverse/nflreadr", ref = "dev")
```

## Roadmap

This package `must` include:

-   Functions for loading:
    -   general `rds_from_url()`, `qs_from_url()`, `parquet_from_url()`
        ✅
    -   pbp ✅
    -   player\_stats (aggregated by week ~~or season~~) ✅
    -   schedules (aka Lee’s game data) ✅
    -   rosters ✅
    -   team\_stats (aggregated by week ~~or season~~)
    -   Next Gen Stats data ✅
-   Document the available package options (currently nflreadr.cache and
    nflreadr.prefer) somewhere. Maybe in `nflreadr-package.R` created
    with `use_package_doc()`?
-   CRAN (because we want to introduce it as a dependency for other
    packages)

It would be nice if this package included:

-   Memoised/cached data by default ✅
-   ~~Optional parallel processing (?) -&gt; we can do this with
    `parallel::mclapply()` in combination with `do.call("rbind", ...)`
    to avoid the `future` and `furrr` dependencies~~ ❌ *slower than
    not-parallel*

Design decisions:

-   depend directly on qs as primary? adds weight but is markedly faster
    than rds ✅
-   drop parquet support? heavyweight and slower than qs ✅
-   use option to configure rather than file\_type arg? ✅
