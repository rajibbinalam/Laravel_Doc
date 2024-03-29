### PHP Date Formating

```php
  <?php
    // Assuming today is March 10th, 2001, 5:16:18 pm, and that we are in the
    // Mountain Standard Time (MST) Time Zone

    $today = date("F j, Y, g:i a");                 // March 10, 2001, 5:16 pm
    
    $today = date("m.d.y");                         // 03.10.01
    
    $today = date("j, n, Y");                       // 10, 3, 2001
    
    $today = date("Ymd");                           // 20010310
    
    $today = date('h-i-s, j-m-y, it is w Day');     // 05-16-18, 10-03-01, 1631 1618 6 Satpm01
    
    $today = date('\i\t \i\s \t\h\e jS \d\a\y.');   // it is the 10th day.
    
    $today = date("D M j G:i:s T Y");               // Sat Mar 10 17:16:18 MST 2001
    
    $today = date('H:m:s \m \i\s\ \m\o\n\t\h');     // 17:03:18 m is month
    
    $today = date("H:i:s");                         // 17:16:18
    
    $today = date("h:i:s A");                       // 5:16:18 PM
    
    $today = date("Y-m-d H:i:s");                   // 2001-03-10 17:16:18 (the MySQL DATETIME format)
  ?>

```

### Get First and Last Date of The Current Month:

```php
    $first_day = date('Y-m-01');   $last_day = date('Y-m-t');

```
### Date Diff for Humens
```php
{{ $blog_post->created_at->diffForHumans() }}   <!-- it'll show: 4 Hours Ago -->
{{ optional($item->product)->created_at->diff(\Carbon\Carbon::now())->format('%yY, %mM') }}  // 1Year , 4 Months
```

### Get date of year, previous year, month, previous month, week, previous week
```php
    $startYear = now()->startOfYear();
    
    $prevYear = now()->startOfYear()->subYear();
    
    $startMonth = now()->startOfMonth();
    
    $prevMonth = now()->startOfMonth()->subMonth();

    $startWeek = now()->startOfWeek();
    
    $prevWeek = now()->startOfWeek()->subWeek();

```
### Carbon format:
```php
return \Carbon\Carbon::parse($data->created_at)->format('W');       // For Week
```


### AddMonth or SubMonth => for Laravel
```php

Carbon::now()->subMonth();       // curr_month - 1 Month
Carbon::now()->subMonths(5);      // curr_month - 5 Month

Carbon::now()->addMonth();       // curr_month + 1 Month
Carbon::now()->addMonths(5);    //  curr_month + 5 Month


```
