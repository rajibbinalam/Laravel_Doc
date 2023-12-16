         Laravel Doc: https://laravel.com/docs/8.x/seeding#main-content
                                           
1. Make Model & Migration:
```sh
php artisan make:model Post -m
```

3. Make Factory:

```sh
php artisan make:factory PostFactory
```
----------------- In Factory:--------------------
```php
    protected $model = \App\Models\Post::class;
    public function definition()
    {
        $title = $this->faker->sentence;
        return [
            'title' => $title,
            'description' => $this->faker->text(500),
            'slug' => Str::slug($title),
            'tags' => implode(',', $this->faker->words(5)),
        ];
    }
```
    
3. Make Seeder:
```sh
php artisan make:Seeder PostSeeder
```
---------------- In Seeder : -------------------
```php
        public function run()
        {
           Post::factory()->count(10)->create();
           //Post::factory()->times(10)->create();
           //Post::factory(10)->create();
        }
```
4.----------------- In Database Seeder -------------------
```php
    public function run()
    {
        $this->call([
            UserSeeder::class,
            PostSeeder::class,
        ]);
        // \App\Models\User::factory(10)->create();
    }
```
  5.----DB Seeding: ----  
```sh
php artisan db:seed --class=PostSeeder
php artisan db:seed
```
                            
                            
  
