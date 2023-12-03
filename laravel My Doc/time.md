### Adding time and Subtruct time with current date and time
```php
$date = date('Y-m-d');
$time = date('h:i A');
$nextDate = Carbon::parse($date)->addDay(1)->format('Y-m-d');

$sub_hours   = Carbon::parse($date . ' ' . $time)->subHours(2)->format('Y-m-d H:i:s');

$add_hours   = Carbon::parse($nextDate . ' ' . $time)->addHours(2)->format('Y-m-d H:i:s');

$sub_minutes = Carbon::parse($date . ' ' . $time)->subMinutes(30)->format('Y-m-d H:i:s');
```



### PHP time formation:
1. d - Day of the month; with leading zeros
2. j - Day of the month; without leading zeros
3. D - Day of the month (Mon - Sun)
4. l - Day of the month (Monday - Sunday)
5. S - English suffix for day of the month (st, nd, rd, th)
6. F - Monthname (January - December)
7. M - Monthname (Jan-Dec)
8. m - Month (01-12)
9. n - Month (1-12)
10. Y - Year (e.g 2013)
11. y - Year (e.g 13)
12. a and A - am or pm
13. g - 12 hour format without leading zeros
14. G - 24 hour format without leading zeros
15. h - 12 hour format with leading zeros
16. H - 24 hour format with leading zeros
17. i - Minutes with leading zeros
18. s - Seconds with leading zeros
19. u - Microseconds (up to six digits)
20. e, O, P and T - Timezone identifier
21. U - Seconds since Unix Epoch (space)
22. '#' - One of the following separation symbol: ;,:,/,.,,,-,(,)
23. ? - A random byte
24. * - Random bytes until next separator/digit
25. ! - Resets all fields to Unix Epoch
26. | - Resets all fields to Unix Epoch if they have not been parsed yet
27. + - If present, trailing data in the string will cause a warning, not an error
