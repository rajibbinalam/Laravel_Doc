## Laravel QA
#### 1. What is resource in laravel?
  ans: resource is a class which is used to convert the database or model into json serializable Data. send from server to the client.
#### 2. What is Guard and policy? and diference between them?
  ans: In Laravel, both guards and policies are used for implementing authentication and authorization in your application. However, they serve different purposes and have distinct roles.

  __Guard:__
  
  A guard in Laravel is responsible for authenticating users and managing user sessions. It determines how users are authenticated and provides the necessary functionality to handle authentication-related tasks. Laravel includes various guard implementations out of the box, such as the session guard, token guard, and JWT guard.
  The guard is configured in the config/auth.php file, where you can specify the authentication driver, session details, and other authentication-related settings. Guards help determine the user's identity and manage the authentication state throughout the application.

  __Policy:__
  
  A policy in Laravel is used for defining authorization rules or access policies for individual models or resources. It allows you to define the rules that determine whether a user is authorized to perform specific actions on a resource. Policies help you centralize and encapsulate authorization logic related to specific models or resources.
  A policy class typically contains authorization methods corresponding to different actions, such as view, create, update, and delete. These methods define the authorization logic based on the user's role, permissions, or other criteria. Policies are often used in conjunction with Laravel's gate feature, which provides a convenient way to perform authorization checks throughout your application.

  __To summarize the difference:__

  __-Guard__ focuses on user authentication and managing the user session. It determines how users are authenticated and provides the       necessary functionality to handle authentication-related tasks.
  
  __-Policy__ , on the other hand, focuses on authorization and defining rules for accessing specific resources. It provides a               centralized place to define authorization logic for individual models or resources.

  In simple terms, guards handle the process of determining who the user is, while policies handle the process of determining what the user is allowed to do. They work together to provide a robust authentication and authorization system in Laravel applications.
#### 3. what is Facades?
<p>facades provide a "static" interface to classes that are available in the application's service container. They act as shortcuts to
 access underlying classes that perform actual work, without needing to manually resolve them from the service container or inject them.

  A facade in Laravel is a class that provides a static-like interface to an object that is managed by the service container.
  
  Each facade has a method ```getFacadeAccessor()``` that tells Laravel what service to resolve from the container.</p>

#### 4. What is ShouldQuiue and Quiable in Quiue? What does these in backend (behind the scene)?

<p>
  In Laravel, when working with queues, the interfaces ShouldQueue and the trait Queueable are used to define how a job (like sending an email, processing an image, etc.) should be handled asynchronously in the background.
  
  ShouldQueue is an interface that tells Laravel:
  "This job should not run immediately; instead, queue it to be processed later."

  Queueable is a trait provided by Laravel that gives a class several helpful methods and properties related to queue behavior.

</p>

#### 5. What's attribute in model?
 __ans__: Laravel model attributes are basically representing the database fields for the given model. When data is retrieved from the database, it can be accessed through the model           as they were actual properties of the model instance: $model->database_column_name .
#### 7. What's interface? Utilize and use.
 __ans__: A PHP interface defines a contract which a class must fulfill.
#### 8. What is model binding and what it does?
  <p>
    Model Binding is a powerful feature in Laravel that automatically injects model instances into your route or controller methods         based on route parameters.
  </p>

__Instead__ of manually querying the database using an ID passed in the URL, Laravel does it for you behind the scenes.
__Example__
```php
// Route
Route::get('/users/{user}', function (App\Models\User $user) {
    return $user;
});
//Controller
public function show(User $user)
{
    return view('users.show', compact('user'));
}
```
#### 9. What Does the boot Method Do in a Laravel Model?
In Laravel Eloquent models, the ```boot()``` method is used to hook into the model's lifecycle events — such as when a model is being created, updated, deleted, etc.
#### 10. Why use Service and what is the benifit of it?
#### 11. If by mistakely 2 Routes are exactly Same. then Explain what will do?
__Ans:__ Laravel will use only the last defined route. The earlier route(s) with the same URI and method are overwritten silently.
#### 12. Dependency Injection in laravel?
__Ans:__ When a class/interface use in a function parameter, this called Dependency Injection.
#### 13. Service provider and Service Container?
__Ans:__ 
1. Service providers are the central place to configure your application. If you open the ```config/app.php``` file included with Laravel, you will see a providers array. These             are all of the service provider classes that will be loaded for your application.
2. The service providers in a Laravel application serve as the core point from which the application is bootstrapped. As a result, providers are used to inject laravel's               basic services into the service container as well as our application's services, classes, and their dependencies into the service container.
#### 14. What's psr and psr4?
__Ans:__ PHP standart recomendation. PSR-4 (Autoloading Standard).  Learn...
1. https://www.php-fig.org/psr/psr-4/    
2. https://www.specbee.com/blogs/introduction-php-standard-recommendation-psr
#### 15. Laravel Magic methods Explaination?
__Ans:__  Find the more Details and in below some method names are considered magical: 
```php
__construct(), __destruct(), __call(), __callStatic(), __get(), __set(), __isset(), __unset(),
__sleep(), __wakeup(), __serialize(), __unserialize(), __toString(), __invoke(), __set_state(),
__clone(), and __debugInfo().
```
#### 15. What is Trait and why it use for?
__Ans:__ Traits are a mechanism for code reuse in single inheritance languages such as PHP.
#### 16. What the deference between self:: and $this?
__Ans:__
  __self::__ is used to access class constants, static properties, and static methods within the context of the class itself. within the static method
```php
class MyClass {
    const MY_CONSTANT = 10;
    public static function printConstant() {
        echo self::MY_CONSTANT;
    }
}
```

   __$this__ is used to refer to the current instance of the class. It can be used to access instance properties and methods. It's commonly used within non-static methods to refer        to the properties and methods specific to the instance of the class that the method is being called on.
```php
class MyClass {
    private $myProperty;
    
    public function setProperty($value) {
        $this->myProperty = $value;
    }
    
    public function getProperty() {
        return $this->myProperty;
    }
}
```
#### 17. What is aggregate in Laravel?
__Ans:__  Laravel includes aggregate functions such as max, min, count, average, and total

#### 18. When we should use query builder instead of Eloquent query?
__Discussion:__ 
    1. Lightweight Operations
    2. Complex SQL Queries
    3. Situations Where ORM Features Are Not Needed
    4. Query Builder is faster because it avoids the overhead of Eloquent model instantiation.
    5. Ideal for large data sets, like exporting 10,000+ rows or running aggregate reports.
__Ans:__ When we want to store as it is to the database like,
 ```php
// This Originial Data that want to store
'{"icon":"<i class=\"fab fa-telegram-plane\"><\/i>","title":"Official Channel","content":"https:\/\/t.me\/fxtraderswide"}'
  
// After Store the data using ```Eloquent Query``` in database
"{\"icon\":\"<i class=\\\"fab fa-telegram-plane\\\"><\\\/i>\",\"title\":\"Official Channel\",\"content\":\"https:\\\/\\\/t.me\\\/fxtraderswide\"}"
  
// After Store the data using ```Query builder``` in database
{"icon":"<i class=\"fab fa-telegram-plane\"><\/i>","title":"Official Channel","content":"https:\/\/t.me\/fxtraderswide"}
```
  So, Query Builder Better In this Situation


#### 19. What is actual different between Throwable $th and Exception $e in laravel try catch.
```php
try {
    // Some code that might throw an Exception or Error
} catch (Exception $e) {
    // This block will catch any Exception and its subclasses
    // But will not catch PHP runtime Errors
} catch (Error $e) {
    // This block can specifically catch PHP runtime Errors
} catch (Throwable $th) {
    // This block will catch both Exceptions and Errors, along with any other Throwable
}
```

#### 20. Global vs Local Scopes
__Answer:__

__Global__ scopes apply constraints to all queries of a model automatically (e.g. a “published” filter). Defined in the model’s booted() method.

__Local__ scopes are reusable query constraints that are applied manually using methods like ```scopePopular()``` called via ```Model::popular()->get()```.

#### 21. Repository Pattern & Action Classes
__Answer:__

__Repository Pattern__ abstracts data access into separate classes, decoupling business logic from persistence and making it easier to test. 
SecondTalent

__Action Classes__ focus on solo, single-purpose tasks (e.g., CreateUser), promoting SRP and clearer testing setups than bloated service classes.

#### 22. Macros — extending Laravel dynamically
__Answer:__ Thanks to the Macroable trait, you can add methods at runtime to classes like Collection, Request, etc. Typically registered in a service provider’s boot() method—perfect for reusable behaviors across your app.

#### 23. Contracts vs Facades
__Answer:__

A Contract is a PHP interface defining a service (e.g., Queue) and encourages dependency injection via interface.

A Facade is a static proxy to a service bound in the container (e.g., Queue::push()).
Contracts define the “what”; facades define the “how” you access it. 
SecondTalent

#### 24. Feature Tests vs Unit Tests
__Answer:__
Unit Tests isolate a small part of the application—no framework bootstrapping.
Feature Tests test integrated behavior via HTTP requests, controllers, and middleware. Use tests/Unit and tests/Feature accordingly.

#### For Advance Question:
https://www.secondtalent.com/interview-guide/php/?utm_source=chatgpt.com
