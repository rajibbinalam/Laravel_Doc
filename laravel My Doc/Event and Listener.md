__For Example : We will Send To all or Single User A Email When Create A new Post__

1. Make Event:  ```php artisan make:event NewsMailProcessed```

2. Make Listener : ```php artisan make:listener SendNewsNotification --event=NewsMailProcessed```

3. Register in EventServiceProvider: 

```
    protected $listen = [
        Registered::class => [
            SendEmailVerificationNotification::class,
        ],
        NewsMailProcessed::class=>[                 // This is
            SendNewsNotification::class,
        ]
    ];
```

4. In Event: create a public variable and construct this ( for receiving Data )
```
    public $data;
    public function __construct($data)
    {
        $this->data = $data;
    }
```

5. In Listner's handle function, Do what you want to do--------- Wanna Send Mail to User

```
    public function handle(NewsMailProcessed $event)
    {
        // if you want send Email to all User
        foreach(User::all() as $user){
            Mail::to($user->email)->send(new NewsEventMail($event->data));      // NewsEventMail is a Mail
        }

        // For Sngle Auth User
        // Mail::to(auth()->user()->email)->send(new NewsEventMail($event->data));
    }
```

6. Design your Mail and View For Sending Mail (  See the Mail Part if need )

7. Call the Event in NewsController when News Create:

```
event(new NewsProcessed(['title'=>$request->name, 'slug'=> $request->slug, 'message'=>'New Post Created']));
```
