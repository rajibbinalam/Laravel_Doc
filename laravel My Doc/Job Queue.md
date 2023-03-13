### Laravel Queue run and implements with event listeners

##### 1. Make Queue table and Migrate the Table
```php
php artisan queue:table
php artisan migrate
```

##### 2. In .ENV Change This
```php
QUEUE_CONNECTION=database
```
##### 3. Je Mail Queueable hobe Oitar Class e implements ShouldQueue:  
```php
class NewsEventMail extends Mailable implements ShouldQueue
``` 
##### 4. run this command:
```php 
php artisan queue:listen
```
##### 5. Start work queue will auto.
