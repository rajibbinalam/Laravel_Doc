```php
$faker = Faker::create();
 for($i = 0; $i<=100; $i++){
    User::create([
        'name' => $faker->name,
        'email' => $faker->unique()->safeEmail,
        'password' => $faker->password,
    ]);
}
```
```sh
php artisan tinker
User::factory()->count(10)->create();
```
// Faker Provide So many Dumy Text
// 1. Name
// 2. Email (unique()->safeEmail)
// 3. address
// 4. password
// 5. state
// 6. country
// 7. phone
// 8. date
// 9. 
// 10.
// 11.
