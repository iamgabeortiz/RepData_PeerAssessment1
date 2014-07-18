# Reproducible Research: Peer Assessment 1

## Loading and preprocessing the data

```r
## #############################################################################
# Reproducible Research: Peer Assessment 1 / PA1_template.Rmd
#
# Gabriel Ortiz / gabeortiz@icloud.com
#
# Completes course project objectives by answering questions.
#
## #############################################################################
## Assumptions
#       1. You have set your working directory to the coure project folder.
#       2. You did not move the activity.zip file from the folder root.
#
#
## #############################################################################
## Assumption
#       This function will take in a working directory string, file url string,
#       file name and import function type and load up your data file.
#
## Args
#       wd:     working directory
#       lf:     local file
#       fu:     file url
#       fN:     file name
#       it:     import type
#       uf:     unzip file
#       zf:     zip filename
#
## Return
#       data.frame

load.data <- function(wd, lf = T, fu, fn, it = "csv", uf = F, zf, ... ){
        # set working directory
        setwd(wd)
        
        # check if data folder exists and create it if not
        if(!file.exists("./data")){ dir.create("./data") }
        
        # create variable to store local file path
        df <- paste0("./data/", fn)
        
        # download the file
        if(lf == F){ download.file(fu, destfile = df) }
        
        # unzip the file
        unzip(zf, exdir = "./data")
        
        # read the data using the indicated import type
        if(it == "csv"){ x <- read.csv(df) }
        
        # return data.frame
        return(x)
}

## load the course data file
activity <- load.data(
        getwd(),
        lf = T,
        "N/A",
        "activity.csv",
        it = "csv",
        uf = T,
        "activity.zip"
        )

## add a Date formatted column
activity$realdate <- as.Date(activity$date)
```

After we load up the data file, we see what our data frame is all about.

```r
names(activity)
```

```
## [1] "steps"    "date"     "interval" "realdate"
```

```r
str(activity)
```

```
## 'data.frame':	17568 obs. of  4 variables:
##  $ steps   : int  NA NA NA NA NA NA NA NA NA NA ...
##  $ date    : Factor w/ 61 levels "2012-10-01","2012-10-02",..: 1 1 1 1 1 1 1 1 1 1 ...
##  $ interval: int  0 5 10 15 20 25 30 35 40 45 ...
##  $ realdate: Date, format: "2012-10-01" "2012-10-01" ...
```

```r
head(activity, 10)
```

```
##    steps       date interval   realdate
## 1     NA 2012-10-01        0 2012-10-01
## 2     NA 2012-10-01        5 2012-10-01
## 3     NA 2012-10-01       10 2012-10-01
## 4     NA 2012-10-01       15 2012-10-01
## 5     NA 2012-10-01       20 2012-10-01
## 6     NA 2012-10-01       25 2012-10-01
## 7     NA 2012-10-01       30 2012-10-01
## 8     NA 2012-10-01       35 2012-10-01
## 9     NA 2012-10-01       40 2012-10-01
## 10    NA 2012-10-01       45 2012-10-01
```
## What is mean total number of steps taken per day?



## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
