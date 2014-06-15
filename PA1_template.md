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

Group the number of steps taken per day.


```r
steps_per_day = aggregate(steps ~ date, raw_data, sum)
```

### Histogram


```r
hist(steps_per_day$steps, main="Histogram of number of steps per day", xlab="Steps per day", breaks=8)
```

![plot of chunk steps_per_day_hist](figure/steps_per_day_hist.png) 

### Mean


```r
mean(steps_per_day$steps)
```

```
## [1] 10766
```

### Median


```r
median(steps_per_day$steps)
```

```
## [1] 10765
```

## What is the average daily activity pattern?

Group the number of steps taken per interval.


```r
data_without_na = subset(raw_data, !is.na(raw_data$steps))
steps_per_interval = aggregate(steps ~ interval, data_without_na, mean)
```

Plot the data.


```r
plot(steps_per_interval$interval, steps_per_interval$steps, type="l")
```

![plot of chunk steps_per_interval_plot](figure/steps_per_interval_plot.png) 

The time interval, on average across all the day in the dataset, that contains
the maximum number of steps is:


```r
row_with_most_average_steps <- which.max(steps_per_interval$steps)
steps_per_interval[row_with_most_average_steps,]$interval
```

```
## [1] 835
```

## Imputing missing values


## Are there differences in activity patterns between weekdays and weekends?
