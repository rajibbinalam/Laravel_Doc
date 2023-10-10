## Reqquest in Laravel

### Get Query String from address bar
```blade
{{ request()->getQueryString() }}  => // company_id=1&department_id=&designation_id=&employee_full_id=&month=2023-09
```
### Get Server or Domain
```php
Request::server("SERVER_NAME") => // '127.0.0.1' (For Local)
```
