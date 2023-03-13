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



## Make a JOB ( after steps 1,2 )
##### 1.1. Make jobe
```php
php artisan make:job JobName     //ex: SendEmails
```
##### 1.2. Define your Logics in handle function of the job Ex:
```php
public function handle()
{
$subscribers = User::all()->toArray();

foreach ($subscribers as $subscriber)
{
    \Mail::send('emails.blog', ['post' => $this->post, 'subscriber' => $subscriber], function ($m) use($subscriber) {
        $m->to($subscriber['email'], $subscriber['name']);
        $m->subject('A new article has been published.');
    });
}
```
##### 1.3. Dispatch your job where you want to use the job ( Ex: after a post create send a Email to all Users )
```php
public function store(Request $request){
  //...... Create Post
  SendEmails::dispatch($post);
  // OR $this->dispatch( (new onPostPublished($post))->onQueue('emails') );
}
```
##### 1.4. Do Step 4 for running the queue



#### For Linux -> Supervisore :: [supervisore](https://learn2torials.com/a/how-to-setup-laravel-supervisor)
