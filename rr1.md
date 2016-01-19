# Reproducible Research: Peer Assessment 1

```r
library(lattice)
```




## 1. Loading and preprocessing the data
Load data activity.csv and convert dates to R Date class  

```r
activity_data <- read.csv("activity.csv")
```

```
## Warning in file(file, "rt"): kann Datei 'activity.csv' nicht öffnen: No
## such file or directory
```

```
## Error in file(file, "rt"): kann Verbindung nicht öffnen
```

```r
activity_data$date <- as.Date(activity_data$date,"%Y-%m-%d")
```

```
## Error in as.Date(activity_data$date, "%Y-%m-%d"): Objekt 'activity_data' nicht gefunden
```
Change language settings to English

```r
Sys.setenv(LANG = 'en')
Sys.setlocale("LC_TIME", "English")
```

```
## [1] "English_United States.1252"
```




## 2. Histogram of total number of steps per day and mean / median of steps per day
Compute total number of steps per day  

```r
total_steps_per_day <- tapply(activity_data$steps, activity_data$date,sum)
```

```
## Error in tapply(activity_data$steps, activity_data$date, sum): object 'activity_data' not found
```
Plot histogram of total number of steps per day

```r
hist(total_steps_per_day,col="red",xlab="Total Steps per Day", 
      ylab="Frequency", main="Histogram of Total Steps taken per day")
```

```
## Error in hist(total_steps_per_day, col = "red", xlab = "Total Steps per Day", : object 'total_steps_per_day' not found
```
Compute Mean total steps taken per day

```r
mean(total_steps_per_day,na.rm=TRUE)
```

```
## Error in mean(total_steps_per_day, na.rm = TRUE): object 'total_steps_per_day' not found
```

Compute Median total steps taken per day

```r
median(total_steps_per_day,na.rm=TRUE)
```

```
## Error in median(total_steps_per_day, na.rm = TRUE): object 'total_steps_per_day' not found
```

## 3. Average daily activity pattern
Compute mean of steps over all days by time interval

```r
mean_steps_by_interval <- tapply(activity_data$steps,activity_data$interval,
                                 mean,na.rm=TRUE)
```

```
## Error in tapply(activity_data$steps, activity_data$interval, mean, na.rm = TRUE): object 'activity_data' not found
```
Timeseries plot of of the 5-minute interval and the average number of steps taken, averaged across all days

```r
plot(row.names(mean_steps_by_interval),mean_steps_by_interval,type="l",
     xlab="Time Intervals (5-minute)", 
     ylab="Mean number of steps taken (all Days)", 
     main="Average number of Steps Taken at different 5 minute Intervals",
     col="blue")
```

```
## Error in row.names(mean_steps_by_interval): object 'mean_steps_by_interval' not found
```
Time interval e interval that contains maximum average number of steps over all days

```r
interval_num <- which.max(mean_steps_by_interval)
```

```
## Error in which.max(mean_steps_by_interval): object 'mean_steps_by_interval' not found
```

```r
interval_max_steps <- names(interval_num)
```

```
## Error in eval(expr, envir, enclos): object 'interval_num' not found
```

```r
interval_max_steps
```

```
## Error in eval(expr, envir, enclos): object 'interval_max_steps' not found
```










