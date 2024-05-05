* ## What is PSR?
PHP Standards Recommendations (PSR) are a set of standards that PHP developers should follow to write clean, readable, and maintainable code
like:
  
1. psr-3 responsible for logging. 
2. psr-4 responsible for autoloading classes. 
3. psr-6 responsible for caching. 
4. psr-12 responsible for coding style guide.

* ## What is Composer?
Composer is a dependency manager for PHP. It allows you to declare the libraries your project depends on and it will manage (install/update) them for you.

* ## What is the difference between require and require_once?
`require` and `require_once` are both used to include a file in the current script. 
The difference is that `require_once` will check if the file has already been included and if so, it will not include it again.

* ## What is the difference between var_dump and print_r?
`var_dump` displays structured information about one or more expressions that includes its type and value.

`print_r` displays information about a variable in a way that's readable by humans.

* ## What is the difference between == and ===?
`==` is an equality operator that compares two values and returns `true` if they are equal.

`===` is an identity operator that compares two values and returns `true` if they are equal and of the same type.

* ## Does PHP support multiple inheritance?
No. PHP only supports multi-level inheritance.

example to illustrate the difference between multiple and multi-level inheritance in PHP:

<details>

<summary>Multiple Inheritance (Not Supported in PHP)</summary>

```php
// Parent Class 1
class ParentClass1 {
    public function method1() {
        return "Method 1 from ParentClass1";
    }
}

// Parent Class 2
class ParentClass2 {
    public function method2() {
        return "Method 2 from ParentClass2";
    }
}

// Child Class attempting to use multiple inheritance
// This will result in a syntax error in PHP
class ChildClass extends ParentClass1, ParentClass2 {
    // Class body
}
```
</details>

<details>

<summary>Multi-level Inheritance (Supported in PHP)</summary>

```php
// Grandparent Class
class GrandparentClass {
    public function method1() {
        return "Method 1 from GrandparentClass";
    }
}

// Parent Class inheriting from GrandparentClass
class ParentClass extends GrandparentClass {
    public function method2() {
        return "Method 2 from ParentClass";
    }
}

// Child Class inheriting from ParentClass
class ChildClass extends ParentClass {
    // Class body
}

// Create an instance of ChildClass
$childObj = new ChildClass();

// Access methods from GrandparentClass and ParentClass
echo $childObj->method1();  // Output: Method 1 from GrandparentClass
echo $childObj->method2();  // Output: Method 2 from ParentClass
```
</details>

* ## Is HTTP protocol stateless or stateful?
HTTP (HyperText Transfer Protocol) is a stateless protocol. This means that each request is independent and unrelated to the previous or subsequent requests.

* ## What is a session?
A session is a way to store information (in variables) to be used across multiple pages. By default, session variables last until the user closes the browser.

* ## What is a cookie?
A cookie is a small piece of data that is stored on the user's computer by the web browser while browsing a website. Cookies are used to remember stateful information or to track user activity.

* ## What is more secure session or cookie? and why?
Sessions are generally considered more secure than cookies because the session data is stored on the server and not on the client's computer.

also session is encrypted by default, while cookies can be encrypted but it's not the default behavior.

* ## How does the server read the session or cookies from the user browser?
The server reads the session data from the user's browser by using a session ID. The session ID is stored in a cookie or passed as a URL parameter. The server uses this session ID to retrieve the session data stored on the server.

* ##  What is the difference between class and interface?
1. Interfaces do not contain business logic
2. You must extend the interface to use. 
3. You can't create an object of the interface.

* ## What is a Scope Resolution Operator?
The Scope Resolution Operator `::` is used to access class constants or static properties and methods.

* ## What are Static properties?
Static properties cannot be accessed through the object using the arrow operator `->`.

Declaring class properties or methods as static makes them accessible without needing an instantiation of class

* ## What are Magic Methods?
Magic methods are special methods built into PHP that are called automatically when certain conditions are met like

`__construct`, `__destruct`, `__get`, `__set`, `__isset`, `__unset`, `__call`, `__callStatic`, `__toString`, `__invoke`, `__set_state`, `__clone`, `__sleep`, `__wakeup`, `__serialize`, `__unserialize`, `__debugInfo`.

* ## What’s the difference between unset() and unlink()?
`unset()` used to unset a variable.

`unlink()` used to delete a file from the file system.

* ## How can we get the number of elements in an array?
You can use the `count()` function to get the number of elements in an array.

* ##  What is the difference between $_GET and $_POST?
`$_GET` is an associative array of variables passed to the current script via the URL parameters.

`$_POST` is an associative array of variables passed to the current script via the HTTP POST method.

* ## How to check if two objects are extended from the same parent or class?
You can use the `instanceof` operator.

* ## Overriding vs Overloading?
Overriding is when a child's class redefines a method from the parent class.

Overloading is when a single method behaves differently based on the number or type of arguments passed to it.

* ## Does PHP support Overloading?
No, PHP does not support method overloading.

if you try to define two methods with the same name in a class. you will have a fatal error.

<details>

<summary>Not Supported Overloading</summary>

```php

class SampleClass
{
	function add(int $a, int $b): int
	{
		return $a + $b;
	}

	function add(int $a, int $b, int $c): int
	{
		return $a + $b + $c > 10 ?? 10;
	}
}

// Fatal error: Cannot redeclare SampleClass::add()

```
</details>

you can use `func_get_args()` to get all arguments passed to a function.

You can only overload methods using the magic method __call

<details>

<summary>Example of using the magic method __call</summary>

```php
class SampleClass
{
    function __call($name, $arguments)
    {
        if ($name == 'add') {
            if (count($arguments) == 2) {
                return $this->addTwo(...$arguments);
            } elseif (count($arguments) == 3) {
                return $this->addThree(...$arguments);
            }
        }
    }

    function addTwo(int $a, int $b): int
    {
        return $a + $b;
    }

    function addThree(int $a, int $b, int $c): int
    {
        return $a + $b + $c > 10 ?? 10;
    }
}

$sample = new SampleClass();

echo $sample->add(1, 2); // Output: 3
echo $sample->add(1, 2, 3); // Output: 6
```

</details>

* ##  What is PHP Trait?
A Trait is simply a group of methods that you want to include within another class.
A Trait, like an abstract class, cannot be instantiated on its own.
The main benefit of traits is their reusable nature.
The PHP language is a single inheritance language

<details>

<summary>Example</summary>

```php
trait SharePost {
  public function share($item)
  {
    return 'share this post;
  }
}

class Post {
  use SharePost;
}

$post = new Post();

echo $post->share('post'); // Output: share this post
```

</details>

* ## What is the Design pattern?
A general repeatable solution to a commonly occurring problem in software design.

* ## What is the difference between pass-by-value and pass-by-reference?
Pass by value means that a copy of the variable is passed to the function,

while pass by reference means that the actual variable is passed to the function.
it is kind of made it has global variable if you change anything in the pass by reference,
so you are changing it outside the function scope

Also, if you pass an object as a variable, this is pass by reference 

<details>

<summary>Pass by value</summary>

```php
function printString($string) {
    $string = "This is pass by value"."\n";
 
    print($string);
}
  
$string = "Global Value"."\n";
printString($string);
print($string);

// Output:
// This is pass by value
// Global Value

```

</details>

<details>

<summary>Pass by reference</summary>

```php
function printString(&$string) {
    $string = "This is pass by reference"."\n";
 
    print($string);
}

$string = "Global Value"."\n";

printString($string);
print($string);

// Output:
// This is pass by reference
// This is pass by reference

```

</details>

* ## How to catch any exception in PHP?
You can use the `throwable` interface to catch any exception in PHP.

<details>

<summary>Example</summary>

```php
try {
    // Code that may throw an exception
} catch (Throwable $e) {
    // Catch any exception
    echo 'Caught exception: ',  $e->getMessage(), "\n";
}
```

</details>

* ## What is arrow function in PHP?
Arrow functions are a more concise way of writing anonymous functions in PHP.

<details>

<summary>Example</summary>

```php
$numbers = [1, 2, 3, 4, 5];

// Using traditional anonymous function
$filtered = array_filter($numbers, function ($num) {
    return $num % 2 === 0;
});

// Using arrow function
$filtered = array_filter($numbers, fn($num) => $num % 2 === 0);
```

</details>

* ## Give me example of match expression in PHP?

Match expression is a more concise and readable way to compare a value against many different values in PHP.

<details>

<summary>Example</summary>

```php
$day = 'Monday';

// Using traditional switch statement
switch ($day) {
    case 'Monday':
        echo 'Start of the week';
        break;
    case 'Friday':
        echo 'End of the week';
        break;
    default:
        echo 'Middle of the week';
}

// Using match expression
echo match ($day) {
    'Monday' => 'Start of the week',
    'Friday' => 'End of the week',
    default => 'Middle of the week',
};
```

</details>

* ## Is match faster than switch in PHP?

Yes, match is faster than switch in PHP
because match is a more optimized and concise way to compare a value against many different values.

* ## can we define properties in interfaces in PHP?

Yes, you can define properties in interfaces in PHP.


<details>

<summary>Example</summary>

```php
interface SampleInterface
{
    public const NAME = 'John Doe';
}

echo SampleInterface::NAME; // Output: John Doe
```

</details>

* ## How to test static method in PHPUnit mocking?

You can use the `setStaticExpectations` method in PHPUnit to test static methods.

<details>

<summary>Example</summary>

```php
class SampleClass
{
    public static function add(int $a, int $b): int
    {
        return $a + $b;
    }
}

class SampleTest extends TestCase
{
    public function testAdd()
    {
        $this->staticExpects(SampleClass::class)
            ->method('add')
            ->with(1, 2)
            ->willReturn(3);

        $result = SampleClass::add(1, 2);

        $this->assertEquals(3, $result);
    }
}
```

</details>

* ## you have a bug on production and you have access to database and logs, how do you debug it?

1. Check the logs for any error messages or exceptions.
2. Check the database for any incorrect data or missing records.
3. Use debugging tools like Xdebug to step through the code and identify the issue.
4. Use print statements to log the values of variables and functions to identify the issue.
5. Use profiling tools like Blackfire to identify performance bottlenecks.
6. Use monitoring tools like New Relic to identify any performance issues.
7. Use version control to identify any recent changes that may have caused the bug.
8. Use error tracking tools like Sentry to identify and track errors in production.
