### Laravel QA
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

  To summarize the difference:

  -Guard focuses on user authentication and managing the user session. It determines how users are authenticated and provides the necessary functionality to handle authentication-related tasks.
  
  -Policy, on the other hand, focuses on authorization and defining rules for accessing specific resources. It provides a centralized place to define authorization logic for individual models or resources.

  In simple terms, guards handle the process of determining who the user is, while policies handle the process of determining what the user is allowed to do. They work together to provide a robust authentication and authorization system in Laravel applications.
#### 3. what is Facades?
#### 4. What is ShouldQuiue and Quiable in Quiue? What does these in backend (behind the scene)?
#### 5. What's attribute in model?
#### 6. What's Service Provider and Service Container?
#### 7. What's interface?
#### 8. What is model binding and what it does?
#### 9. What to do `boot` method in model?
#### 10. Why use Service and what is the benifit of it?
#### 11. If by mistakely 2 Routes are exactly Same. then Explain what will do?
#### 12. Dependency Injection in laravel?
#### 13. Service provider and Service Container?

