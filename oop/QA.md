## OOP some tricks question and answer (Find the answer below or search in Chat GPT)

### 1. how to change a private variable value of a class creating a new instance?
ANS:
In (OOP), private variables are intended to be accessed and modified only within the class where they are declared. However, you can provide public methods, known as "setter" methods, to modify the private variable values indirectly.

```php
class MyClass {
    private $privateVariable;

    public function __construct($initialValue) {
        $this->privateVariable = $initialValue;
    }

    public function setPrivateVariable($newValue) {
        $this->privateVariable = $newValue;
    }
}

// Creating an instance of MyClass
$myObject = new MyClass('initial value');

// Accessing the private variable indirectly using the 'setter method'
$myObject->setPrivateVariable('new value');

```

### 2. how can i change private variable value of a class which is inherited from other class?
ANS:
In OOP, if a private variable is declared in a parent class and you want to change its value in a child class, you have a few options:

i. Protected or Getter/Setter Methods:
        Declare the private variable as protected instead of private in the parent class. Protected variables are accessible to child classes, allowing them to directly modify the value
        
```php
class ParentClass {
    protected $privateVariable;

    public function setPrivateVariable($newValue) {
        $this->privateVariable = $newValue;
    }
}

class ChildClass extends ParentClass {
    public function changePrivateVariable($newValue) {
        $this->privateVariable = $newValue;
    }
}

// Usage
$childObject = new ChildClass();
$childObject->changePrivateVariable('new value');
```
ii. Protected Getter and Setter Methods:
        If you want to keep the private variable as private in the parent class, you can define protected getter and setter methods in the parent class. These methods allow the child class to indirectly modify the private variable

```php
class ParentClass {
    private $privateVariable;

    protected function setPrivateVariable($newValue) {
        $this->privateVariable = $newValue;
    }
}

class ChildClass extends ParentClass {
    public function changePrivateVariable($newValue) {
        $this->setPrivateVariable($newValue);
    }
}

// Usage
$childObject = new ChildClass();
$childObject->changePrivateVariable('new value');
```

### 3. What is Getter and Setter Methods (accessors and mutators)
ANS:
Getter and setter methods, also known as accessors and mutators, are methods used to retrieve (get) and modify (set) the values of private or protected variables in a class. They provide a way to access and manipulate the state of an object while maintaining encapsulation and controlling access to the variables

### 4. What is Access Modifier?
ANS:
Access modifiers (or access specifiers) are keywords in object-oriented languages that set the accessibility of classes, methods, and other members. 
Ex: 

__public:__ Can Access `public` Property : 1. Inside 2. Class Object instence 3. Sub Class

__private:__ Can Access `private` Property : 1. Inside

__protected:__ Can Access `protected` Property : 1. Inside 3. Sub Class

```php
class User{
    public $name = 'Rajib';
    final public function userInfo(){
        echo $this->name;               // 1. This is Inside
    }
}
-----------------------------------------------
class Admin extends User{
    public function userInfo(){
        echo $this->name;            // 2. This is Inherit (Sub Class)
    }
}
-----------------------------------------------

$user = new User;
$user->name;                        // 3. This is Object instence
```
### 5. What the deference between `self::` and `$this`?
ANS: `self::` is use for static property of a class. and `$this` is used for other property of a class.

<b> 🟥 NB: for static function access by a class Instence => `className::functionName`. </b>
### 6. How to Prevent Extending(inherit) of a class & Overriding a Method of a Class?
ANS: Use `final` keyword;
__In Class__
```php
final class User{     // This Class can't be inherit or extends
}
```
__In Method__
```php
class ParentClass {
    final public function myMethod() {
        // Method implementation Final Keyword
    }
}

class ChildClass extends ParentClass {
    // Attempting to override the final method will result in an error
    public function myMethod() {
        // New implementation - Error: Cannot override final method
    }
}
```
### 6. Abstract Classes?
ANS: An abstract class is a class that contains at least one abstract method. An abstract method is a method that is declared, but not         implemented in the code.

  __Rules:__
  
    1. The child class method must be defined with the same name and it redeclares the parent abstract method
    
    2. The child class method must be defined with the same or a less restricted access modifier
    
    3. The number of required arguments must be the same. However, the child class may have optional arguments in addition

### 7. Can i instantiate an abstract class in php?
ANS: No, you cannot directly instantiate an abstract class in PHP. Abstract classes are meant to be used as blueprints for other             classes, and they typically contain abstract methods that must be implemented by any concrete (non-abstract) subclass. Abstract          classes themselves cannot be instantiated because they are incomplete and may have methods that lack implementations. abstract           classes is to serve as a blueprint for concrete subclasses
### 8. A abstract class can extends another abstract class in php?
ANS: Yes, in PHP, an abstract class can extend another abstract class.
```php
abstract class Animal {
    abstract public function makeSound();
}

abstract class Mammal extends Animal {
    abstract public function giveBirth();
}

class Dog extends Mammal {
    public function makeSound() {
        return "Woof!";
    }

    public function giveBirth() {
        return "Gives birth to live puppies.";
    }
}
```
### 9. Abstraction vs. Interfaces:
ANS: 
1. Abstract classes can have both abstract and concrete methods, while interfaces can only define method signatures (no method implementations).

2. A class can extend only one abstract class but can implement multiple interfaces.

### 10. Can you declare a private/ protected method in an interface?
ANS: NO, All methods or Access modifiers declared in an interface must be public.
### 11. Interface Inheritance:
ANS: Interfaces can extend other interfaces using the extends keyword.
