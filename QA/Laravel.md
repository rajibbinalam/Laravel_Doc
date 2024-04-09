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
#### 4. What is ShouldQuiue and Quiable in Quiue? What does these in backend (behind the scene)?
#### 5. What's attribute in model?
    ans: Laravel model attributes are basically representing the database fields for the given model. When data is retrieved from the database, it can be accessed through the model           as they were actual properties of the model instance: $model->database_column_name .
#### 7. What's interface? Utilize and use.
    ans: A PHP interface defines a contract which a class must fulfill.
#### 8. What is model binding and what it does?
#### 9. What to do `boot` method in model?
#### 10. Why use Service and what is the benifit of it?
#### 11. If by mistakely 2 Routes are exactly Same. then Explain what will do?
#### 12. Dependency Injection in laravel?
    ans: When a class/interface use in a function parameter, this called Dependency Injection.
#### 13. Service provider and Service Container?
    ans: 1. Service providers are the central place to configure your application. If you open the config/app. php file included with Laravel, you will see a providers array. These             are all of the service provider classes that will be loaded for your application.
         2. The service providers in a Laravel application serve as the core point from which the application is bootstrapped. As a result, providers are used to inject laravel's               basic services into the service container as well as our application's services, classes, and their dependencies into the service container.
#### 14. What's psr and psr4?
    ans: PHP standart recomendation. PSR-4 (Autoloading Standard).  Learn...
         1. https://www.php-fig.org/psr/psr-4/    2. https://www.specbee.com/blogs/introduction-php-standard-recommendation-psr
#### 15. Laravel Magic methods Explaination?
    ans:  Find the more Details and in below some method names are considered magical: 
```php
__construct(), __destruct(), __call(), __callStatic(), __get(), __set(), __isset(), __unset(),
__sleep(), __wakeup(), __serialize(), __unserialize(), __toString(), __invoke(), __set_state(),
__clone(), and __debugInfo().
```
#### 15. What is Trait and why it use for?
    ans: Traits are a mechanism for code reuse in single inheritance languages such as PHP.
#### 16. What the deference between self:: and $this?
    ans: 
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
    ans:  Laravel includes aggregate functions such as max, min, count, average, and total

#### 18. When we should use query builder instead of Eloquent query?
    Discussion: 
    1. Lightweight Operations
    2. Complex SQL Queries
    3. Situations Where ORM Features Are Not Needed
    
    ans: When we want to store as it is to the database like,
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
