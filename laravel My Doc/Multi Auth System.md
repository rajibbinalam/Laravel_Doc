# Multi Auth System Using ```Guard```
#### 1. New Laravel Install

#### 2. Laravel Ui install for custom user login

#### 3. Make Model & Migrate for Admin and run Migrate
```sh
php artisan make:model Admin -m
```
#### 4. Make 2 Controller
	1. Backend/Admin 
 	2. Backend/Dashboard
#### 5. Make 2 View File 
	1. Backend/Admin/login 
 	2. Backend/Dashboard/admin_dashboard ( use Bootstrap )
#### 6. Make 2 Route 
	1. Login form view 
 	2. Dashboard view
#### 7. In Controller view 
	1. login form 
 	2. Dashboard
#### 8. In Admin Model ------------ Copy From User Model: 
	1. [use Illuminate\Foundation\Auth\User as Authenticable ]
	2. [class Admin extends Authenticable 3. $fillable, $hidden ]

#### 9. In Config/Auth.php 
```php
// 1. guards=>
	'admin'=>[
		'driver'=>'session',
		'provider' => 'admin',
		],
// 2. provider => 
	'admins'=>[
		'driver'=>'eloquent',
		'model'=> App\Models|Admin::class,
		],
```
#### 10. make: Middleware (Admin)
```sh
php artisan make:middleware Admin
```
#### 11. In app/Http/kernel.php -- Protected $routeMiddleware=[
	'admin'=>\App\Http\Middleware\Admin::class,

#### 12. In Middleware -- In handle Function
	1. if(!Auth::guard('admin')->check()){
		return redirect('admin/login');
	   }
	   return $next($request);
	2. use Auth;

#### 13. Make: Form Submit Route & Controller Cedentials 
 	1. Route::post('admin/login'[adminController::class,'login']);
	2. In Controller: 
		*** validation--------
		if(Auth::guard('admin')->attempt(['email'=>$request->email , 'password'=>$request->password])){
			return redirect()->route('admin.dashboard');
		}else{
			Session::flash('error','Invalid Email or Password');
			return redirect()->back();
		}

#### 14. For error_msg Print: 
	@if(Session::has('error')
		<p class="text-danger">{{ Session::get('error')}}</p>
	 @else
	 @endif

#### 15. For Logout: 
```php
//In Route 
Route::get('admin/logout',[AdminController::class,'AdminLoguot']);

// In Controller
public function AdminLogout(){
	Auth::guard('admin')->logout();
	return redirect('admin/login');
} 
		
```



