### Web.php
```php
routes('blogs', 'App\Http\Controllers\BlogController', true);
```
### helper.php
```php
use Illuminate\Support\Facades\Log;
use Illuminate\Support\Facades\Route;


function routes($route, $controller, $resource = false, $middleware = 'web'){
    if(!class_exists($controller)){
        Log::error($controller . ' not found');
    }
    if($resource){
        Route::resource($route, $controller)->middleware($middleware);
        return;
    }else{
        Route::get('/'.$route, $controller.'@index')->middleware($middleware);
        return;
    }
}
```
Make More:
1. make a package for routes
2. write all routes in the package and call from the router or change the router file path
