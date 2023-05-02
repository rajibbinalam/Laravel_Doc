### Use Multiple Database in a Single Project

1. in .env
```php
DB_HOST_SECOND="DB HOST HERE"
DB_PORT_SECOND="DB PORT HERE"
DB_DATABASE_SECOND="DATABASE NAME HERE"
DB_USERNAME_SECOND="DB USERNAME HERE"
DB_PASSWORD_SECOND="DB PASSWORD HERE"
```
2. Configure database detail in config / database.php
```php
<?php

return [
   'connections'=>[
     'mysql'=>[
       'driver' => 'mysql',
       'url' => env('DATABASE_URL'),
       'host' => env('DB_HOST', '127.0.0.1'),
       'port' => env('DB_PORT', '3306'),
       'database' => env('DB_DATABASE', 'forge'),
       'username' => env('DB_USERNAME', 'forge'),
       'password' => env('DB_PASSWORD', ''),
     ],
     'mysql_second'=>[
       'driver' => 'mysql',
       'url' => env('DATABASE_URL'),
       'host' => env('DB_HOST_SECOND', '127.0.0.1'),
       'port' => env('DB_PORT_SECOND', '3306'),
       'database' => env('DB_DATABASE_SECOND', 'forge'),
       'username' => env('DB_USERNAME_SECOND', 'forge'),
       'password' => env('DB_PASSWORD_SECOND', ''),
     ]
   ]
];

?>
```
3. Schema Builder
```php
Schema::connection('mysql_second')->create('table_name', function($table){
   // entire code here
});

// Query Bulder
$posts = \DB::connection('mysql_second')->select('id','title')->get();
```

4. Eloquent Model
```php
<?php

namespace App\Models;

class Post extends Eloquent {
   protected $connection = 'mysql_second';
}

?>

// Query Bulder
\DB::table('posts')->join('mysql_second.types as secondDbType','posts.code','=','secondDbType.code')->first();
```


More Resources: https://techvblogs.com/blog/how-to-use-multiple-database-connections-in-laravel
