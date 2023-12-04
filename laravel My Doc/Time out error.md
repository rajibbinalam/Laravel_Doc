### Php or laravel large data processing Time out error/ issues
__Export Huge data in Excel Like 16k+__

Use this in Controller where call the Excel for Export;

```php
ini_set('max_execution_time', 0);

ini_set('memory_limit', '-1');

ini_set("pcre.backtrack_limit", "50000000");
```
