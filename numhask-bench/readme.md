numhask-bench
=============

[![Build
Status](https://travis-ci.org/tonyday567/numhask-bench.png)](https://travis-ci.org/tonyday567/numhask-bench)

array performance
-----------------

The first runs compares creation of a 10x10 matrix and matrix
multiplication for:

-   [hmatrix](http://hackage.haskell.org/package/hmatrix)
-   [matrix](https://hackage.haskell.org/package/matrix)
-   A NumHask.Array instance with list as a container
-   A NumHask.Array instance with a boxed vector instance

<!-- -->

    square matrix size: 10

    creation
    hmatrix:                  7.80e4
    matrix:                   2.74e3
    Array []:                 2.90e4
    Array Vector(Boxed):      5.32e4

    mmult
    run                        first      2nd      3rd   median      av.

    hmatrix                   1.32e4   7.15e3   2.38e3   2.18e3   3.37e3
    matrix                    3.69e4   1.97e4   1.98e4   1.84e4   2.23e4
    []                        1.76e4   2.32e2   1.96e2   1.41e2   8.18e2
    Boxed                     1.83e4   7.01e3   6.44e3   6.23e3   9.24e3

All measurements are in cycles. See
[perf](https://hackage.haskell.org/package/perf) for what this is. The
runs show the first three measurements, then the median and average of
many runs.

NumHask.Array operations
------------------------

    square matrix size: 10
    run                        first      2nd      3rd   median      av.

    row                       4.73e3   9.50e2   4.44e2   3.59e2   3.69e2
    col                       1.52e3   3.86e2   1.82e2   1.26e2   4.70e2
    unsafeRow                 1.34e3   1.40e2   4.00e1   3.84e1   4.05e1
    unsafeCol                 5.08e2   1.38e2   1.14e2   1.12e2   8.13e2
    unsafeIndex               3.47e3   4.32e2   2.06e2   1.84e2   1.98e2
    concat                    2.48e4   8.89e3   8.01e3   7.18e3   1.28e4
    transpose                 3.80e2   5.80e1   2.60e1   2.22e1   2.33e1

recipe
------

    stack build --exec "$(stack path --local-install-root)/bin/numhask-bench" --exec "$(stack path --local-bin)/pandoc -f markdown -i other/bench_.md -t markdown -o readme.md --filter pandoc-include --mathjax" --file-watch

reference
---------

-   [perf](https://hackage.haskell.org/package/perf)
-   [numhask](https://hackage.haskell.org/package/numhask)

