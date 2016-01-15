    ## Inputting the data ...
    ## Perform Quality Control assessment of the LumiBatch object ...

SOME PLOTS OF NON NORMALIZED DATA: density plot, cdf plot ![](raw-data-analysis_files/figure-markdown_github/unnamed-chunk-3-1.png) ![](raw-data-analysis_files/figure-markdown_github/unnamed-chunk-3-2.png) ![](raw-data-analysis_files/figure-markdown_github/unnamed-chunk-3-3.png) ![](raw-data-analysis_files/figure-markdown_github/unnamed-chunk-3-4.png)

    ## Perform vst transformation ...
    ## 2016-01-14 17:11:58 , processing array  1 
    ## 2016-01-14 17:11:58 , processing array  2 
    ## 2016-01-14 17:11:59 , processing array  3 
    ## 2016-01-14 17:11:59 , processing array  4 
    ## 2016-01-14 17:11:59 , processing array  5 
    ## 2016-01-14 17:11:59 , processing array  6 
    ## 2016-01-14 17:11:59 , processing array  7 
    ## 2016-01-14 17:11:59 , processing array  8 
    ## 2016-01-14 17:11:59 , processing array  9 
    ## 2016-01-14 17:11:59 , processing array  10 
    ## 2016-01-14 17:11:59 , processing array  11 
    ## 2016-01-14 17:11:59 , processing array  12 
    ## Perform rsn normalization ...
    ## 2016-01-14 17:12:00 , processing array  1 
    ## 2016-01-14 17:12:00 , processing array  2 
    ## 2016-01-14 17:12:00 , processing array  3 
    ## 2016-01-14 17:12:00 , processing array  4 
    ## 2016-01-14 17:12:00 , processing array  5 
    ## 2016-01-14 17:12:00 , processing array  6 
    ## 2016-01-14 17:12:00 , processing array  7 
    ## 2016-01-14 17:12:00 , processing array  8 
    ## 2016-01-14 17:12:00 , processing array  9 
    ## 2016-01-14 17:12:00 , processing array  10 
    ## 2016-01-14 17:12:01 , processing array  11 
    ## 2016-01-14 17:12:01 , processing array  12 
    ## Perform Quality Control assessment of the LumiBatch object ...

PLOTS OF NORMALIZED DATA

![](raw-data-analysis_files/figure-markdown_github/unnamed-chunk-4-1.png) ![](raw-data-analysis_files/figure-markdown_github/unnamed-chunk-4-2.png) ![](raw-data-analysis_files/figure-markdown_github/unnamed-chunk-4-3.png) FILTERING PROBES BASED ON DETECTION Limma suggests to keep probes that are expressed above bg on at least n arrays where n is smallest number of replicates assigned to any of the treatment combinations.

how many probes did we have before and after filtering?

    ##          detection exprs se.exprs
    ## Features     47323 47323    47323
    ## Samples         12    12       12

    ##          detection exprs se.exprs
    ## Features     19305 19305    19305
    ## Samples         12    12       12

how many removed?

    ##          detection exprs se.exprs
    ## Features     28018 28018    28018
    ## Samples          0     0        0

Here's the design matrix for the analysis

    ##    concentration0 concentration5 concentration50 concentration500 donorB
    ## 1               1              0               0                0      0
    ## 2               0              1               0                0      0
    ## 3               0              0               1                0      0
    ## 4               0              0               0                1      0
    ## 5               1              0               0                0      1
    ## 6               0              1               0                0      1
    ## 7               0              0               1                0      1
    ## 8               0              0               0                1      1
    ## 9               1              0               0                0      0
    ## 10              0              1               0                0      0
    ## 11              0              0               1                0      0
    ## 12              0              0               0                1      0
    ##    donorC
    ## 1       0
    ## 2       0
    ## 3       0
    ## 4       0
    ## 5       0
    ## 6       0
    ## 7       0
    ## 8       0
    ## 9       1
    ## 10      1
    ## 11      1
    ## 12      1
    ## attr(,"assign")
    ## [1] 1 1 1 1 2 2
    ## attr(,"contrasts")
    ## attr(,"contrasts")$concentration
    ## [1] "contr.treatment"
    ## 
    ## attr(,"contrasts")$donor
    ## [1] "contr.treatment"

Here's the contrasts matrix

    ##                   Contrasts
    ## Levels             MaxVsCtrl MidVsCtrl MinVsCtrl
    ##   concentration0          -1        -1        -1
    ##   concentration5           0         0         1
    ##   concentration50          0         1         0
    ##   concentration500         1         0         0
    ##   donorB                   0         0         0
    ##   donorC                   0         0         0

How many probes are up and down regulated for each contrast?

    ## Source: local data frame [3 x 3]
    ## 
    ##    variable down up
    ## 1 MaxVsCtrl    0  0
    ## 2 MidVsCtrl    0  0
    ## 3 MinVsCtrl    0  0

![](raw-data-analysis_files/figure-markdown_github/unnamed-chunk-11-1.png)

Some probes of interest from MTN-007.

![](raw-data-analysis_files/figure-markdown_github/unnamed-chunk-12-1.png)

SessionInfo()

    ## R version 3.2.1 (2015-06-18)
    ## Platform: x86_64-w64-mingw32/x64 (64-bit)
    ## Running under: Windows 7 x64 (build 7601) Service Pack 1
    ## 
    ## locale:
    ## [1] LC_COLLATE=English_United States.1252 
    ## [2] LC_CTYPE=English_United States.1252   
    ## [3] LC_MONETARY=English_United States.1252
    ## [4] LC_NUMERIC=C                          
    ## [5] LC_TIME=English_United States.1252    
    ## 
    ## attached base packages:
    ## [1] parallel  stats     graphics  grDevices utils     datasets  methods  
    ## [8] base     
    ## 
    ## other attached packages:
    ## [1] ggplot2_1.0.1.9003  reshape2_1.4.1      limma_3.24.14      
    ## [4] lumi_2.20.2         Biobase_2.28.0      BiocGenerics_0.14.0
    ## [7] dplyr_0.4.2        
    ## 
    ## loaded via a namespace (and not attached):
    ##  [1] tidyr_0.2.0             nor1mix_1.2-1          
    ##  [3] splines_3.2.1           foreach_1.4.2          
    ##  [5] bumphunter_1.8.0        assertthat_0.1         
    ##  [7] affy_1.46.1             stats4_3.2.1           
    ##  [9] doRNG_1.6               Rsamtools_1.20.4       
    ## [11] methylumi_2.14.0        yaml_2.1.13            
    ## [13] minfi_1.14.0            RSQLite_1.0.0          
    ## [15] lattice_0.20-33         quadprog_1.5-5         
    ## [17] digest_0.6.8            GenomicRanges_1.20.5   
    ## [19] RColorBrewer_1.1-2      XVector_0.8.0          
    ## [21] colorspace_1.2-6        htmltools_0.2.6        
    ## [23] preprocessCore_1.30.0   Matrix_1.2-2           
    ## [25] plyr_1.8.3              GEOquery_2.34.0        
    ## [27] siggenes_1.42.0         XML_3.98-1.3           
    ## [29] biomaRt_2.24.0          genefilter_1.50.0      
    ## [31] zlibbioc_1.14.0         xtable_1.7-4           
    ## [33] scales_0.2.5.9003       affyio_1.36.0          
    ## [35] BiocParallel_1.2.14     nleqslv_2.8            
    ## [37] annotate_1.46.1         beanplot_1.2           
    ## [39] pkgmaker_0.22           mgcv_1.8-7             
    ## [41] IRanges_2.2.5           GenomicFeatures_1.20.1 
    ## [43] lazyeval_0.1.10         survival_2.38-3        
    ## [45] magrittr_1.5            mclust_5.0.2           
    ## [47] evaluate_0.7.2          nlme_3.1-121           
    ## [49] MASS_7.3-43             BiocInstaller_1.18.4   
    ## [51] tools_3.2.1             registry_0.3           
    ## [53] formatR_1.2             matrixStats_0.14.2     
    ## [55] stringr_1.0.0           S4Vectors_0.6.2        
    ## [57] munsell_0.4.2           locfit_1.5-9.1         
    ## [59] rngtools_1.2.4          AnnotationDbi_1.30.1   
    ## [61] lambda.r_1.1.7          Biostrings_2.36.1      
    ## [63] base64_1.1              GenomeInfoDb_1.4.1     
    ## [65] futile.logger_1.4.1     grid_3.2.1             
    ## [67] RCurl_1.95-4.7          iterators_1.0.7        
    ## [69] labeling_0.3            bitops_1.0-6           
    ## [71] rmarkdown_0.7           gtable_0.1.2           
    ## [73] codetools_0.2-14        multtest_2.24.0        
    ## [75] DBI_0.3.1               reshape_0.8.5          
    ## [77] R6_2.1.0                illuminaio_0.10.0      
    ## [79] GenomicAlignments_1.4.1 knitr_1.11             
    ## [81] rtracklayer_1.28.6      futile.options_1.0.0   
    ## [83] KernSmooth_2.23-15      stringi_0.5-5          
    ## [85] Rcpp_0.12.1
