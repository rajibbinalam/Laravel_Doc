### All of Date in Laravel

#### Difference Between two Dates, Months, Years
```php
$toDate = Carbon::parse("2021-08-10");
$fromDate = Carbon::parse("2022-08-20");

$days = $toDate->diffInDays($fromDate);
$months = $toDate->diffInMonths($fromDate);
$years = $toDate->diffInYears($fromDate);
```
