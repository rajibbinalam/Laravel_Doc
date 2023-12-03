#### When a project is running on cPanel but not run on local Server then try
```sh
php -S localhost:8000
```

#### Share a Laravel Project from Local in same Network
```bash
#Run project for share
php artisan serve --host=YourIp (ex:198.0.0.1)

#Access from another device in same Network
YourIp:8000 (Ex: 198.0.0.1:8000)
