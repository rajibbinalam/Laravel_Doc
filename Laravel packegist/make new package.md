1. make folder in root of the project
2. goto inside of it and ```composer init```
		-- set up your info. 
##### OR use package skeleton from spatie
3. Configure your composer.json file
	-- NB: name of psr-4 is the namespace of the package ex: ```"Rajib\\LaravelSlugGenerator\\"```
4. write or copy Package Discovery in composer.json
```php
// after -> "require": {},
"extra": {
        "laravel": {
            "providers": [
                "Rajib\\LaravelSlugGenerator\\SlugGeneratorServiceProvider"
            ],
            "aliases": {
                "SlugGenerator": "Rajib\\LaravelSlugGenerator\\SlugGenerator"
            }
        }
    }
```

5. make service Provider in src folder.
6. set the namespace and class name and register and boot method:  __see the ServiceProvider Doc__
```php
<?php

namespace Rajib\LaravelSlugGenerator;

use Illuminate\Support\ServiceProvider;

class SlugGeneratorServiceProvider extends ServiceProvider
{
    /**
     * Register any application services.
     */
    public function register(): void
    {
        //
    }



    /**
     * Bootstrap any application services.
     */
    public function boot(): void
    {
       //
    }
}
```

7. make a file in src folder: ex: SlugGenerator.php => write your all codes here
```php
<?php

namespace Rajib\LaravelSlugGenerator;

class SlugGenerator
{
    /**
     * Generate a Unique Slug.
     *
     * @param object $model
     * @param string $title
     * @param string $field
     * @param string $separator
     *
     * @return string
     * @throws \Exception
     */
    public function generate($model, $title, $field, $separator = "-"): string
    {
        $id = 0;

        $slug =  preg_replace('/\s+/', $separator, (trim(strtolower($title))));
        $slug =  preg_replace('/\?+/', $separator, (trim(strtolower($slug))));
        $slug =  preg_replace('/\#+/', $separator, (trim(strtolower($slug))));
        $slug =  preg_replace('/\/+/', $separator, (trim(strtolower($slug))));

        // $slug = preg_replace('!['.preg_quote($separator).']+!u', $separator, $title);

        // Remove all characters that are not the separator, letters, numbers, or whitespace.
        // $slug = preg_replace('![^'.preg_quote($separator).'\pL\pN\s]+!u', '', mb_strtolower($slug));

        // Replace all separator characters and whitespace by a single separator
        $slug = preg_replace('![' . preg_quote($separator) . '\s]+!u', $separator, $slug);

        // Get any that could possibly be related.
        // This cuts the queries down by doing it once.
        $allSlugs = $this->getRelatedSlugs($slug, $id, $model, $field);

        // If we haven't used it before then we are all good.
        if (!$allSlugs->contains("$field", $slug)) {
            return $slug;
        }

        // Just append numbers like a savage until we find not used.
        for ($i = 1; $i <= 10; $i++) {
            $newSlug = $slug . $separator . $i;
            if (!$allSlugs->contains("$field", $newSlug)) {
                return $newSlug;
            }
        }

        throw new \Exception('Can not create a unique slug');
    }

    private function getRelatedSlugs($slug, $id, $model, $field)
    {
        if (empty($id)) {
            $id = 0;
        }

        return $model::select("$field")->where("$field", 'like', $slug . '%')
            ->where('id', '<>', $id)
            ->get();
    }
}
```

8. make Facades Folder and file inside folder in src folder : code below
```php
<?php

namespace Rajib\LaravelSlugGenerator\Facades;

use Illuminate\Support\Facades\Facade;
use Rajib\LaravelSlugGenerator\SlugGenerator as LaravelSlugGeneratorSlugGenerator;

/**
 * @see LaravelSlugGeneratorSlugGenerator;
 */
class SlugGenerator extends Facade
{


    /**
     * Get the registered name of the component.
     *
     * @return string
     */
    protected static function getFacadeAccessor(): string
    {
        return 'Laravel-Slug-Generator';
    }
}
```

9. bind this Facades in register in ServiceProvider
```php
$this->app->bind('Laravel-Slug-Generator', function($app){
            return new \Rajib\LaravelSlugGenerator\SlugGenerator();
        });
```

10. add repositories in composer.json for use this package localy(not live)
```php

"repositories": [
        {
            "type": "path",
            "url": "./laravel-slug-generator"
        }
    ],

// and Add this to "require-dev":
"require-dev": {
	"rajib/laravel-slug-generator": "*"
}
```

11. ```composer install and composer du``` in the package folder terminal

12. add ```"Rajib\\LaravelSlugGenerator\\": "laravel-slug-generator\/src"``` in ```"autoload-dev":``` for Run Localy and ```composer du``` in laravel project


13. in config/app.php => add preovider and aliases

```php
    'providers' => [
	Rajib\LaravelSlugGenerator\SlugGeneratorServiceProvider::class,
]

    'aliases' => [
	'SlugGenerator' => Rajib\LaravelSlugGenerator\Facades\SlugGenerator::class,
]
```
14. composer du and now we can test with tinker or Routes:
```php
SlugGenerator::generate(App\Models\User::class, 'User2', 'username')  // SlugGenerator -> this is Facades Class 
```

15. Make config/example.php (If we need)=> this return array
```php
<?php
return [

    /*
     |----------------------------------------
     |  Default Separator for Slug
     | ----------------------------------------
     |
     |  Default Separator is '-'.
     |
     |*/
     'separator' => '-',
    /*
     |----------------------------------------
     |  Max Unique Slug Count for Same Title
     | ----------------------------------------
     |
     |  Default is '100'. Slug will generate like:
     |  'test-1', 'test-2', 'test-3', ...... 'test-100'
     |
     |*/
     'max_count' => '100',

];
```

16. For Publish the config => in service provider
```php
	//----- in boot method
	$this->publishes([
            __DIR__.'/../config/SlugGenerator.php' => config_path('SlugGenerator.php'),
        ]);

	//----- in register method -- For Merge Config
	$this->mergeConfigFrom(
            __DIR__.'/../config/SlugGenerator.php', 'SlugGenerator'
        );

```

17. web can publish vendor of our package
```php
php artisan publish:vendor
// if does not change old data after trying publish vendor 2nd time then:
php artisan publish:vendor --force
```
