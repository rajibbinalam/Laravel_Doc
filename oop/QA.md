### OOP some tricks question and answer (Find the answer below or search in Chat GPT)

#### 1. how to change a private variable value of a class creating a new instance?
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

#### 2. how can i change private variable value of a class which is inherited from other class?
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

#### 3. What is Getter and Setter Methods (accessors and mutators)
ANS:
Getter and setter methods, also known as accessors and mutators, are methods used to retrieve (get) and modify (set) the values of private or protected variables in a class. They provide a way to access and manipulate the state of an object while maintaining encapsulation and controlling access to the variables

#### 4. What is Access Modifier?
ANS:
Access modifiers (or access specifiers) are keywords in object-oriented languages that set the accessibility of classes, methods, and other members. Ex: public, private, protected
