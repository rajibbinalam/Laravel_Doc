### Adding time and Subtruct time with current date and time
```php
$date = date('Y-m-d');
$time = date('h:i A');
$nextDate = Carbon::parse($date)->addDay(1)->format('Y-m-d');

$sub_hours   = Carbon::parse($date . ' ' . $time)->subHours(2)->format('Y-m-d H:i:s');

$add_hours   = Carbon::parse($nextDate . ' ' . $time)->addHours(2)->format('Y-m-d H:i:s');

$sub_minutes = Carbon::parse($date . ' ' . $time)->subMinutes(30)->format('Y-m-d H:i:s');
```
