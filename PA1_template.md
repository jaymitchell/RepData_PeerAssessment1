# Reproducible Research: Peer Assessment 1



## Loading and preprocessing the data

Extract the data if it is not already extracted.


```r
unzip(paste("data", "activity.zip", sep="/"), exdir="data", overwrite=FALSE)
```

```
## Warning: not overwriting file 'data/activity.csv
```

Read the data from the extracted file.


```r
extracted_filename = paste("data", "activity.csv", sep="/")
raw_data = read.csv(extracted_filename)
```

## What is mean total number of steps taken per day?



## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
