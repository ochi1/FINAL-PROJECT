    library(readr)
    library(dplyr)

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

    library(tidyverse)

    ## ── Attaching packages ─────────────────────────── tidyverse 1.3.0 ──

    ## ✔ ggplot2 3.2.1     ✔ purrr   0.3.3
    ## ✔ tibble  2.1.3     ✔ stringr 1.4.0
    ## ✔ tidyr   1.0.0     ✔ forcats 0.4.0

    ## ── Conflicts ────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

    library(ggplot2)
    library(gridExtra)

    ## 
    ## Attaching package: 'gridExtra'

    ## The following object is masked from 'package:dplyr':
    ## 
    ##     combine

Recent Grads
------------

    recentgrads <- read_csv("Data/recentgrads.csv")

    ## Warning: Missing column names filled in: 'X1' [1]

    ## Parsed with column specification:
    ## cols(
    ##   .default = col_double(),
    ##   Major = col_character(),
    ##   Major_category = col_character()
    ## )

    ## See spec(...) for full column specifications.

    head(recentgrads)

    ## # A tibble: 6 x 22
    ##      X1  Rank Major_code Major Total   Men Women Major_category ShareWomen
    ##   <dbl> <dbl>      <dbl> <chr> <dbl> <dbl> <dbl> <chr>               <dbl>
    ## 1     1     1       2419 PETR…  2339  2057   282 Engineering         0.121
    ## 2     2     2       2416 MINI…   756   679    77 Engineering         0.102
    ## 3     3     3       2415 META…   856   725   131 Engineering         0.153
    ## 4     4     4       2417 NAVA…  1258  1123   135 Engineering         0.107
    ## 5     5     5       2405 CHEM… 32260 21239 11021 Engineering         0.342
    ## 6     6     6       2418 NUCL…  2573  2200   373 Engineering         0.145
    ## # … with 13 more variables: Sample_size <dbl>, Employed <dbl>,
    ## #   Full_time <dbl>, Part_time <dbl>, Full_time_year_round <dbl>,
    ## #   Unemployed <dbl>, Unemployment_rate <dbl>, Median <dbl>, P25th <dbl>,
    ## #   P75th <dbl>, College_jobs <dbl>, Non_college_jobs <dbl>,
    ## #   Low_wage_jobs <dbl>

    recentgrads$recent_total <- recentgrads$Total
    recentgrads$Total <- NULL

    recentgrads$recent_men <- recentgrads$Men
    recentgrads$Men <- NULL

    recentgrads$recent_women <- recentgrads$Women
    recentgrads$Women <- NULL

    #recentgrads$recent_ShareWomen <- recentgrads$ShareWomen
    #recentgrads$ShareWomen <- NULL

    recentgrads$recent_sample_size <- recentgrads$Sample_size
    recentgrads$Sample_size <- NULL

    recentgrads$recent_employed <- recentgrads$Employed
    recentgrads$Employed <- NULL

    recentgrads$recent_full_time <- recentgrads$Full_time
    recentgrads$Full_time <- NULL

    recentgrads$recent_part_time <- recentgrads$Part_time
    recentgrads$Part_time <- NULL

    recentgrads$recent_full_time_year_round <- recentgrads$Full_time_year_round
    recentgrads$Full_time_year_round <- NULL

    recentgrads$recent_unemployed <- recentgrads$Unemployed
    recentgrads$Unemployed <- NULL

    recentgrads$recent_unemployment_rate <- recentgrads$Unemployment_rate
    recentgrads$Unemployment_rate <- NULL

    recentgrads$recent_median <- recentgrads$Median
    recentgrads$Median <- NULL

    recentgrads$recent_p25th <- recentgrads$P25th
    recentgrads$P25th <- NULL

    recentgrads$recent_p75th <- recentgrads$P75th
    recentgrads$P75th <- NULL

    recentgrads$recent_college_jobs <- recentgrads$College_jobs
    recentgrads$College_jobs <- NULL

    recentgrads$recent_non_college_jobs <- recentgrads$Non_college_jobs
    recentgrads$Non_college_jobs <- NULL

    recentgrads$recent_low_wage_jobs <- recentgrads$Low_wage_jobs
    recentgrads$Low_wage_jobs <- NULL

    head(recentgrads)

    ## # A tibble: 6 x 22
    ##      X1  Rank Major_code Major Major_category ShareWomen recent_total
    ##   <dbl> <dbl>      <dbl> <chr> <chr>               <dbl>        <dbl>
    ## 1     1     1       2419 PETR… Engineering         0.121         2339
    ## 2     2     2       2416 MINI… Engineering         0.102          756
    ## 3     3     3       2415 META… Engineering         0.153          856
    ## 4     4     4       2417 NAVA… Engineering         0.107         1258
    ## 5     5     5       2405 CHEM… Engineering         0.342        32260
    ## 6     6     6       2418 NUCL… Engineering         0.145         2573
    ## # … with 15 more variables: recent_men <dbl>, recent_women <dbl>,
    ## #   recent_sample_size <dbl>, recent_employed <dbl>,
    ## #   recent_full_time <dbl>, recent_part_time <dbl>,
    ## #   recent_full_time_year_round <dbl>, recent_unemployed <dbl>,
    ## #   recent_unemployment_rate <dbl>, recent_median <dbl>,
    ## #   recent_p25th <dbl>, recent_p75th <dbl>, recent_college_jobs <dbl>,
    ## #   recent_non_college_jobs <dbl>, recent_low_wage_jobs <dbl>

All Grads
---------

    allgrads <- read_csv("Data/allgrads.csv")

    ## Warning: Missing column names filled in: 'X1' [1]

    ## Parsed with column specification:
    ## cols(
    ##   X1 = col_double(),
    ##   Major_code = col_double(),
    ##   Major = col_character(),
    ##   Major_category = col_character(),
    ##   all_total = col_double(),
    ##   all_employed = col_double(),
    ##   all_employed_full_time_year_round = col_double(),
    ##   all_unemployed = col_double(),
    ##   all_unemployment_rate = col_double(),
    ##   all_median = col_double(),
    ##   all_p25th = col_double(),
    ##   all_p75th = col_double()
    ## )

    head(allgrads)

    ## # A tibble: 6 x 12
    ##      X1 Major_code Major Major_category all_total all_employed
    ##   <dbl>      <dbl> <chr> <chr>              <dbl>        <dbl>
    ## 1     1       1100 GENE… Agriculture &…    128148        90245
    ## 2     2       1101 AGRI… Agriculture &…     95326        76865
    ## 3     3       1102 AGRI… Agriculture &…     33955        26321
    ## 4     4       1103 ANIM… Agriculture &…    103549        81177
    ## 5     5       1104 FOOD… Agriculture &…     24280        17281
    ## 6     6       1105 PLAN… Agriculture &…     79409        63043
    ## # … with 6 more variables: all_employed_full_time_year_round <dbl>,
    ## #   all_unemployed <dbl>, all_unemployment_rate <dbl>, all_median <dbl>,
    ## #   all_p25th <dbl>, all_p75th <dbl>

    allgrads$all_total <- allgrads$Total

    ## Warning: Unknown or uninitialised column: 'Total'.

    allgrads$Total <- NULL

    allgrads$all_employed <- allgrads$Employed

    ## Warning: Unknown or uninitialised column: 'Employed'.

    allgrads$Employed <- NULL

    allgrads$all_employed_full_time_year_round <- allgrads$Employed_full_time_year_round

    ## Warning: Unknown or uninitialised column: 'Employed_full_time_year_round'.

    allgrads$Employed_full_time_year_round <- NULL

    allgrads$all_unemployed <- allgrads$Unemployed

    ## Warning: Unknown or uninitialised column: 'Unemployed'.

    allgrads$Unemployed <- NULL

    allgrads$all_unemployment_rate <- allgrads$Unemployment_rate

    ## Warning: Unknown or uninitialised column: 'Unemployment_rate'.

    allgrads$Unemployment_rate <- NULL

    allgrads$all_median <- allgrads$Median

    ## Warning: Unknown or uninitialised column: 'Median'.

    allgrads$Median <- NULL

    allgrads$all_p25th <- allgrads$P25th

    ## Warning: Unknown or uninitialised column: 'P25th'.

    allgrads$P25th <- NULL

    allgrads$all_p75th <- allgrads$P75th

    ## Warning: Unknown or uninitialised column: 'P75th'.

    allgrads$P75th <- NULL

Grad students
-------------

    gradstudents <- read_csv("Data/gradstudents.csv")

    ## Warning: Missing column names filled in: 'X1' [1]

    ## Parsed with column specification:
    ## cols(
    ##   .default = col_double(),
    ##   Major = col_character(),
    ##   Major_category = col_character()
    ## )

    ## See spec(...) for full column specifications.

    allgrads <- read_csv("Data/allgrads.csv")

    ## Warning: Missing column names filled in: 'X1' [1]

    ## Parsed with column specification:
    ## cols(
    ##   X1 = col_double(),
    ##   Major_code = col_double(),
    ##   Major = col_character(),
    ##   Major_category = col_character(),
    ##   all_total = col_double(),
    ##   all_employed = col_double(),
    ##   all_employed_full_time_year_round = col_double(),
    ##   all_unemployed = col_double(),
    ##   all_unemployment_rate = col_double(),
    ##   all_median = col_double(),
    ##   all_p25th = col_double(),
    ##   all_p75th = col_double()
    ## )

    head(gradstudents)

    ## # A tibble: 6 x 23
    ##      X1 Major_code Major Major_category Grad_total Grad_sample_size
    ##   <dbl>      <dbl> <chr> <chr>               <dbl>            <dbl>
    ## 1     1       5601 CONS… Industrial Ar…       9173              200
    ## 2     2       6004 COMM… Arts                53864              882
    ## 3     3       6211 HOSP… Business            24417              437
    ## 4     4       2201 COSM… Industrial Ar…       5411               72
    ## 5     5       2001 COMM… Computers & M…       9109              171
    ## 6     6       3201 COUR… Law & Public …       1542               22
    ## # … with 17 more variables: Grad_employed <dbl>,
    ## #   Grad_full_time_year_round <dbl>, Grad_unemployed <dbl>,
    ## #   Grad_unemployment_rate <dbl>, Grad_median <dbl>, Grad_P25 <dbl>,
    ## #   Grad_P75 <dbl>, Nongrad_total <dbl>, Nongrad_employed <dbl>,
    ## #   Nongrad_full_time_year_round <dbl>, Nongrad_unemployed <dbl>,
    ## #   Nongrad_unemployment_rate <dbl>, Nongrad_median <dbl>,
    ## #   Nongrad_P25 <dbl>, Nongrad_P75 <dbl>, Grad_share <dbl>,
    ## #   Grad_premium <dbl>

    combinedrecentandgrad <- full_join(recentgrads, gradstudents, by = c("Major_code", "Major", "Major_category"))

    totalcombination <- full_join(combinedrecentandgrad, allgrads, by = c("Major_code", "Major", "Major_category"))

    totalcombination1 <- totalcombination %>% mutate(full_total = all_total + recent_total + Grad_total, full_employed = all_employed + recent_employed + Grad_total, total_unemployed = all_unemployed + recent_unemployed + Grad_unemployed)

    totalcombination2 <- totalcombination1 %>% mutate(full_median = (recent_median + Grad_median + Nongrad_median + all_median)/4)

    totalcombinationpaid <- totalcombination2 %>% arrange(desc(all_median))

    write.csv(totalcombinationpaid, file = "totalcombinationpaid.csv")


    topten <- filter(totalcombination2, all_median > 80000)

    ggplot(data = topten, aes(x = Major, y = all_median)) + geom_bar(stat = "identity") + theme(axis.text.x = element_text(angle = 60, hjust = 1))

![](index_files/figure-markdown_strict/unnamed-chunk-6-1.png)

PLOTTING —————-
===============

### Major Categories

    table(totalcombination2$Major_category)

    ## 
    ##     Agriculture & Natural Resources                                Arts 
    ##                                  10                                   8 
    ##              Biology & Life Science                            Business 
    ##                                  14                                  13 
    ##         Communications & Journalism             Computers & Mathematics 
    ##                                   4                                  11 
    ##                           Education                         Engineering 
    ##                                  16                                  29 
    ##                              Health           Humanities & Liberal Arts 
    ##                                  12                                  15 
    ## Industrial Arts & Consumer Services                   Interdisciplinary 
    ##                                   7                                   1 
    ##                 Law & Public Policy                   Physical Sciences 
    ##                                   5                                  10 
    ##            Psychology & Social Work                      Social Science 
    ##                                   9                                   9

    totalcombination3 <- totalcombination2 %>% mutate(full_unemployment_rate = (recent_unemployment_rate + Grad_unemployment_rate + Nongrad_unemployment_rate + all_unemployment_rate)/4)

    categories <- totalcombination3 %>% group_by(Major_category) %>% summarise(Count = n(), mean_income = mean(full_median), Total = sum(full_total), mean_unemployment = mean(full_unemployment_rate), mean_female = mean(ShareWomen)) %>% arrange(desc(Count))

    #1
    ggplot(data = categories, aes(x = fct_reorder(Major_category, Count, .desc = TRUE), y = Count)) + geom_bar(stat = "identity", fill = "blue") + theme(axis.text.x = element_text(angle = 60, hjust = 1)) + labs(title = "Major Categories", x = "Major Category")

![](index_files/figure-markdown_strict/unnamed-chunk-7-1.png)

    #2
    ggplot(data = categories, aes(x = fct_reorder(Major_category, Total, .desc = TRUE), y = Total)) + geom_bar(stat = "identity", fill = "blue") + theme(axis.text.x = element_text(angle = 60, hjust = 1)) + labs(title = "Total Cases", y = "Cases", x = "Major Category")

    ## Warning: Removed 1 rows containing missing values (position_stack).

![](index_files/figure-markdown_strict/unnamed-chunk-7-2.png) \# 1. In
our dataset, each unique major is classified as one of these 16
categories. Engineering is the most diverse category followed by;
Education, Liberal Arts, Life Science, and Business.

### Major

    mostpopular <- totalcombination3 %>% arrange(desc(full_total)) %>% slice(1:25)

    mostpopularcount <- mostpopular %>% group_by(Major_category) %>% summarise(Count = n()) %>% arrange(desc(Count))

    #3
    ggplot(data = mostpopular, aes(x = fct_reorder(Major, full_total, .desc = TRUE), y = full_total)) + geom_bar(stat = "identity", fill = "green") + theme(axis.text.x = element_text(angle = 75, hjust = 1)) + labs(title = "Popular Majors", x = "Majors", y = "Count")

![](index_files/figure-markdown_strict/unnamed-chunk-8-1.png)

    #4
    ggplot(data = mostpopularcount, aes(x = fct_reorder(Major_category, Count, .desc = TRUE), y = Count)) + geom_bar(stat = "identity", fill = "red") + theme(axis.text.x = element_text(angle = 60, hjust = 1)) + labs(title = "Popular Major Categories", x = "Major Category")

![](index_files/figure-markdown_strict/unnamed-chunk-8-2.png) \#These
are the 25 most popular majors in our dataset. Business Management and
Administration is the most popular with Business being the most popular
category amongst the top 25 majors.

    #5
    ggplot(data = totalcombination2, aes(x = fct_reorder(Major, full_median, .desc = TRUE), y = full_median, color = Major_category)) + geom_point() + labs(main = "Median Income by Major", y = "Median Income", x = "Majors", color = "Major Category") + theme(axis.text.x=element_blank(),
            axis.ticks.x=element_blank())

![](index_files/figure-markdown_strict/unnamed-chunk-9-1.png) \# 4 This
is the median income for all 173 majors we have in our data set. As you
can see, the majors in the categories of Education, Engineering, and
Health are the highest earners.

    #6
    ggplot(data = categories, aes(x = fct_reorder(Major_category, mean_income, .desc = TRUE), y = mean_income)) + geom_bar(stat = "identity", fill = "blue") + theme(axis.text.x = element_text(angle = 60, hjust = 1)) + labs(title = "Income per Major", x = "Major", y = "Median Income")

![](index_files/figure-markdown_strict/unnamed-chunk-10-1.png) \# These
are the average median income for each major category in our dataset. As
you can see engineering is paid the best.

    #7
    ggplot(data = mostpopular, aes(x = fct_reorder(Major, full_median, .desc = TRUE), y = full_median)) + geom_bar(stat = "identity", fill = "red") + theme(axis.text.x = element_text(angle = 60, hjust = 1)) + labs(title = "Income per Major", x = "Major", y = "Median Income")

![](index_files/figure-markdown_strict/unnamed-chunk-11-1.png)

    #8
    ggplot(data = mostpopular, aes(x = fct_reorder(Major_category, full_median, .desc = TRUE), y = full_median)) + geom_boxplot(fill = "yellow") + theme(axis.text.x = element_text(angle = 60, hjust = 1)) + labs(title = "Income for Popular Major Categories", x = "Major Category", y = "Median Income")

![](index_files/figure-markdown_strict/unnamed-chunk-11-2.png) \# 5
majors we want to investigate - General Engineering - Economics -
Political Science and Government - Mathematics - Biology

    ourmajors <- totalcombination3 %>% filter(Major %in% c("GENERAL ENGINEERING", "ECONOMICS", "POLITICAL SCIENCE AND GOVERNMENT", "MATHEMATICS", "BIOLOGY"))

\#Unemployment

    #9
    ggplot(data = totalcombination3, aes(x = fct_reorder(Major, full_unemployment_rate, .desc = TRUE), y = full_unemployment_rate, color = Major_category)) + geom_point() + labs(main = "Unemployment Rate by Major", y = "Unemployment Rate", x = "Majors", color = "Major Category") + theme(axis.text.x=element_blank(),
            axis.ticks.x=element_blank())

![](index_files/figure-markdown_strict/unnamed-chunk-13-1.png)

    #10
    ggplot(data = categories, aes(x = fct_reorder(Major_category, mean_unemployment, .desc = TRUE), y = mean_unemployment)) + geom_bar(stat = "identity", fill = "red") + theme(axis.text.x = element_text(angle = 60, hjust = 1)) + labs(title = "Unemployment by Major Category", x = "Major Category", y = "Unemployment Rate")

![](index_files/figure-markdown_strict/unnamed-chunk-13-2.png)

    #11
    ggplot(data = mostpopular, aes(x = fct_reorder(Major, full_unemployment_rate, .desc = TRUE), y = full_unemployment_rate)) + geom_bar(stat = "identity", fill = "red") + theme(axis.text.x = element_text(angle = 60, hjust = 1)) + labs(title = "Unemployment by Major Category", x = "Major Category", y = "Unemployment Rate")

![](index_files/figure-markdown_strict/unnamed-chunk-13-3.png)

Women
=====

    #12
    ggplot(data = totalcombination3, aes(x = fct_reorder(Major, ShareWomen, .desc = TRUE), y = ShareWomen, color = Major_category)) + geom_point() + labs(main = "% Female", y = "% Female", x = "Majors", color = "Major Category") + theme(axis.text.x=element_blank(),
            axis.ticks.x=element_blank())

    ## Warning: Removed 1 rows containing missing values (geom_point).

![](index_files/figure-markdown_strict/unnamed-chunk-14-1.png)

    #13
    ggplot(data = categories, aes(x = fct_reorder(Major_category, mean_female, .desc = TRUE), y = mean_female)) + geom_bar(stat = "identity", fill = "pink") + theme(axis.text.x = element_text(angle = 60, hjust = 1)) + labs(title = "% Female by Major Category", x = "Major Category", y = "% Female")

    ## Warning: Removed 1 rows containing missing values (position_stack).

![](index_files/figure-markdown_strict/unnamed-chunk-14-2.png)

    #14
    ggplot(data = mostpopular, aes(x = fct_reorder(Major, ShareWomen, .desc = TRUE), y = ShareWomen)) + geom_bar(stat = "identity", fill = "red") + theme(axis.text.x = element_text(angle = 60, hjust = 1)) + labs(title = "% Female by Major Category", x = "Major", y = "% Female")

![](index_files/figure-markdown_strict/unnamed-chunk-14-3.png)

Closer look at our majors
=========================

    #15 
    ggplot(data = ourmajors, aes(x = Major, y = full_median, fill = Major_code)) + geom_bar(stat = "identity") + theme(axis.text.x = element_text(angle = 60, hjust = 1))

![](index_files/figure-markdown_strict/unnamed-chunk-15-1.png)

    #16
    ggplot(data = ourmajors, aes(x = Major, y = full_unemployment_rate, fill = Major_code)) + geom_bar(stat = "identity") + theme(axis.text.x = element_text(angle = 60, hjust = 1))

![](index_files/figure-markdown_strict/unnamed-chunk-15-2.png)

    #17
    ggplot(data = ourmajors, aes(x = Major, y = ShareWomen, fill = Major_code)) + geom_bar(stat = "identity") + theme(axis.text.x = element_text(angle = 60, hjust = 1))

![](index_files/figure-markdown_strict/unnamed-chunk-15-3.png)

    #18
    ggplot(data = ourmajors, aes(x = Major, y = full_median, fill = Major_code)) + geom_bar(stat = "identity") + theme(axis.text.x = element_text(angle = 60, hjust = 1))

![](index_files/figure-markdown_strict/unnamed-chunk-15-4.png)

    #19
    nongrad <- ggplot(data = ourmajors, aes(x = Major, y = Nongrad_median, fill = Major_code)) + geom_bar(stat = "identity") + theme(axis.text.x = element_text(angle = 60, hjust = 1), axis.ticks.x=element_blank())

    grad <- ggplot(data = ourmajors, aes(x = Major, y = Grad_median, fill = Major_code)) + geom_bar(stat = "identity") + theme(axis.text.x = element_text(angle = 60, hjust = 1), axis.ticks.x=element_blank())

    grid.arrange(grad, nongrad)

![](index_files/figure-markdown_strict/unnamed-chunk-15-5.png)

### Plots

    outliers <- totalcombination3 %>%
      filter(full_total >= 310000 | full_median >= 65000)

    ggplot(totalcombination3, aes(Major, full_total)) +
      geom_point() + 
      ggrepel::geom_label_repel(aes(label=paste("(",Major,",",full_median,")"), vjust = 4, hjust = 0, colour = Major_category),
        data = outliers, show.legend = FALSE)

    ## Warning: Removed 1 rows containing missing values (geom_point).

![](index_files/figure-markdown_strict/unnamed-chunk-16-1.png)

    outliers1 <- totalcombination1 %>%
      filter(ShareWomen <= 0 | ShareWomen >=    0.9679982)

    ggplot(totalcombination1, aes(Major, full_total, fill = recent_men)) +
      geom_col() +
      ggrepel::geom_label_repel(aes(label=paste("(",Major,",",recent_men," "," ",recent_low_wage_jobs,")"), vjust = 100, colour = Major_category),
        data = outliers1, show.legend = FALSE)

    ## Warning: Removed 1 rows containing missing values (position_stack).

![](index_files/figure-markdown_strict/unnamed-chunk-17-1.png)

    outliers2 <- totalcombination1 %>%
      filter(recent_unemployment_rate >= .14 | recent_low_wage_jobs >= 25000)

    ggplot(totalcombination1, aes(Major, recent_unemployment_rate)) +
      geom_jitter() +
      ggrepel::geom_label_repel(aes(label=paste("(",Major,",",recent_low_wage_jobs,")"), vjust = 4, hjust = 0, colour = Major_category),
        data = outliers2, show.legend = FALSE)

![](index_files/figure-markdown_strict/unnamed-chunk-18-1.png)
