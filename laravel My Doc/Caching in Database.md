1. For Cache Table:
``` php artisan cache:table ``` and Migrate.
2. Change the CACHE_DRIVER in Cache.php => ``` database```

3. we can Change the Prefix of database table key name from Cache.php  by Changing ```HE_PREFIX```
4. Then Change the ```CACHE_DRIVER=database``` in .env
