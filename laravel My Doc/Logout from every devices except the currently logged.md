### Logout from every devices except the currently logged in last one in Laravel


##### 1. Uncomment ```AuthenticateSession``` from ```app/Http/Kernel.php```

```php
protected $middlewareGroups = [
    'web' => [
        ...
        \Illuminate\Session\Middleware\AuthenticateSession::class,
        ...
    ],
    ...
];
```

##### 2. goto ```LoginController``` and do this == NOTE: if ```authenticated``` function does not exist. then make this

```php
  protected function authenticated(Request $request, $user)
  {
      Auth::logoutOtherDevices($request->password);
  }
```

## Congrates Its work currectly


refer links:

[laravel](https://laravel.com/docs/7.x/authentication#invalidating-sessions-on-other-devices)

[programmingfields](https://programmingfields.com/logout-multiple-login-sessions-from-other-browsers-in-laravel-9/)

[Amit Merchant](https://www.amitmerchant.com/logout-from-everywhere-except-current-device-laravel/)
