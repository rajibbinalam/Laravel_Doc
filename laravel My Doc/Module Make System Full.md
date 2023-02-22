## Make Module System-------

#### 1. Copy-- Commands and stubs Folders__

#### 2. Copy from-- MigrationServiceProvider.php --> for each module and make Changes__

```php
	/*
         |--------------------------------------------------------------------------
         | ADMIN
         |--------------------------------------------------------------------------
        */
        $this->loadMigrationsFrom([
            base_path().DIRECTORY_SEPARATOR.'module'.DIRECTORY_SEPARATOR.'Admin'.DIRECTORY_SEPARATOR.'database'.DIRECTORY_SEPARATOR.'migrations',
        ]);
	
```

#### 3. Copy from-- RouteServiceProvider.php -> See the Chnages__

```php
	<?php

    namespace App\Providers;

    use Illuminate\Http\Request;
    use Illuminate\Support\Facades\Auth;
    use Illuminate\Support\Facades\Route;
    use Illuminate\Cache\RateLimiting\Limit;
    use Illuminate\Support\Facades\RateLimiter;
    use Illuminate\Foundation\Support\Providers\RouteServiceProvider as ServiceProvider;

    class RouteServiceProvider extends ServiceProvider
    {
        /**
        * The path to the "home" route for your application.
        *
        * This is used by Laravel authentication to redirect users after login.
        *
        * @var string
        */
        //_____________________________________________________________________________________change_here
        protected $namespace                    = 'App\Http\Controllers';
        protected $admin                        = 'Module\Admin\Controllers'; //Make this For Each Module
        //protected $admin                        = 'Module\Frontend\Controllers'; 
        //protected $admin                        = 'Module\Hospital\Controllers'; 



        public const HOME = '/home';
        

        /**
        * The controller namespace for the application.
        *
        * When present, controller route declarations will automatically be prefixed with this namespace.
        *
        * @var string|null
        */
        // protected $namespace = 'App\\Http\\Controllers';

        /**
        * Define your route model bindings, pattern filters, etc.
        *
        * @return void
        */

        //_____________________________________________________________________________________change_here
        public function boot()
        {
            parent::boot();		
            // $this->configureRateLimiting();

            // $this->routes(function () {
            //     Route::prefix('api')
            //         ->middleware('api')
            //         ->namespace($this->namespace)
            //         ->group(base_path('routes/api.php'));

            //     Route::middleware('web')
            //         ->namespace($this->namespace)
            //         ->group(base_path('routes/web.php'));
            // });
        }

        /**
        * Configure the rate limiters for the application.
        *
        * @return void
        */

        //_____________________________________________________________________________________change_here
        public function map()
        {
            $this->mapApiRoutes();

            $this->mapWebRoutes();
        }

        /**
        * Define the "web" routes for the application.
        *
        * These routes all receive session state, CSRF protection, etc.
        *
        * @return void
        */
        //_____________________________________________________________________________________change_here
        protected function mapWebRoutes()
        {
            Route::group(['middleware' => 'web'], function () {
		/*
		|--------------------------------------------------------------------------
		| WEB
		|--------------------------------------------------------------------------
		*/
		Route::namespace($this->namespace)->group(base_path('routes/web.php'));

		/*
		|--------------------------------------------------------------------------
		| MODULE WEB
		|--------------------------------------------------------------------------
		*/
                Route::namespace($this->admin)->group(base_path('module/Admin/routes/web.php')); //Make this For Each Module
                //Route::namespace($this->frontend)->group(base_path('module/Frontend/routes/web.php'));
                //Route::namespace($this->hospital)->group(base_path('module/Hospital/routes/web.php'));
            });
        }

        /**
        * Define the "api" routes for the application.
        *
        * These routes are typically stateless.
        *
        * @return void
        */

        //_____________________________________________________________________________________change_here
        protected function mapApiRoutes()
        {
            Route::prefix('api')
                ->middleware('api')
                ->namespace($this->namespace)
                ->group(base_path('routes/api.php'));
        }





        protected function configureRateLimiting()
        {
            RateLimiter::for('api', function (Request $request) {
                return Limit::perMinute(60)->by(optional($request->user())->id ?: $request->ip());
            });
        }
    }
```

#### 4. Register The MigrationServiceProvider in Config>app.php

```php
    App\Providers\MigrationServiceProvider::class,
```

#### 5. Register View of Modules in Config>View.php

```php
    'paths' => [
            resource_path('views'),

            base_path('module/Admin/views'), //Make this For Each Module
            //base_path('module/Frontend/views'),
            //base_path('module/Hospital/views'),
        ],
```
    
#### 6. In Composer.json

```
	"psr-4": {
            "Module\\": "module/",
            "App\\": "app/"
        }
```
#### 7. Composer Dup
```  composer dump-autoload ```
