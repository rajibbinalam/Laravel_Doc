### Check The is local with domain address
```php
if (app('env') == "local" && Request::server("SERVER_NAME") == '127.0.0.1' || Request::server("SERVER_NAME") == 'cybper_poz.test'){
  // 'DO something'
}
```
