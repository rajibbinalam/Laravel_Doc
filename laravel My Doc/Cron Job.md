#### Laravel Cron job 
 ##### 1. make a command and type your functionality in 'handle' function.
 ##### OR
 ##### 1. Make Job Queue Properly.
##### Run Commands
```php

php artisan schedule:run   //  For run the Command
php artisan queue:listen   //  if Schedule have job queue

// THEN 

* * * * * cd /path-to-your-project && php artisan schedule:run >> /dev/null 2>&1

//        OR

//    For Linux Server
php_location: /usr/local/bin/php
file_path   : /home/examplesoftware/domains/example.com/public_html/
Command     : artisan schedule:run >/dev/null 2>&1

/usr/local/bin/php /home/examplesoftware/domains/example.com/public_html/artisan schedule:run >/dev/null 2>&1



//     For Locall:
D:\xampp\php\php.exe D:\xampp\htdocs\project_name\artisan schedule:run

```


##### We can use cron jon another way ( not proper )
###### 1. make a 

