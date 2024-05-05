* ## What is the service container in Laravel?

The Laravel service container is a powerful tool for managing class dependencies and performing dependency injection.

It is a container that holds instances of classes and resolves dependencies automatically.

* ## What is the service provider in Laravel?

Service providers are the central place of all Laravel application bootstrapping.

Your own application, as well as all of Laravel's core services, are bootstrapped via service providers.

* ## What are jobs and when do we use them?

Jobs in Laravel are used to handle asynchronous processing,
allowing the application to perform time-consuming tasks
(like sending emails, processing files, etc.) in the background without blocking the user interface.
Jobs can be pushed onto different queues with varying priorities to be processed by queue workers.


* ## What is CSRF?
**Cross-Site Request Forgery** is a security feature
used to prevent unauthorized actions on a website through forged HTTP requests.
CSRF attacks occur
when a malicious website tricks a user's browser
into sending a request to a different website where the user is authenticated,
without the user's knowledge or consent
It is added by default to web in middleware group variable in Kernel.

Also, you can find it in cookies under the name `XSRF-TOKEN`

* ## What is Fillable Attribute in a Laravel model?
It takes care of defining which fields are to be considered
when the user inserts or updates data

`$fillable` serves as a **white list** of attributes that should be mass assignable,

The `$guarded` property should contain an array of attributes that you do not want to be mass assignable. 

All other attributes not in the array will be mass-assignable. So, $guarded functions like a **black list**

* ## What is Middleware?

Middleware is a mechanism that allows you to filter out HTTP requests entering your application.

For example, Laravel includes a middleware that verifies your application's user is authenticated. 

If the user is not authenticated, the middleware will redirect the user to the login screen. However, 

if the user is authenticated, the middleware will allow the request to proceed further into the application.

* ## What is Facades?

Facades provide a "static" interface to classes that are available in the application's service container.

* ## What is an Active Record?

Active Record is a design pattern
that links business objects and database tables
to create a persistable domain model where the business object contains data retrieval,
data storage, and data manipulation methods.

* ##  What are SQL Injections, how do you prevent them, and what are the best practices?

SQL injection is a type of attack
that occurs when an attacker inserts malicious SQL code into input fields or parameters in a web application's form,
causing the application to execute unintended SQL commands.
This can allow the attacker to access, modify, or delete data from the database

To prevent SQL injection in Laravel: 
- Use Eloquent ORM or Query Builder: it automatically handles input sanitization and parameter binding, which helps prevent SQL injection.
- Use Parameterized Queries: (->where('column', '=', $value)). 
- Avoid Raw Input in Queries: Never concatenate user input directly into your SQL queries. Always sanitize and validate user input before using it in database queries. 
- Use Validation: Validate user input using Laravel's validation rules (validate() method in controllers) to ensure that it meets your application's requirements before using it in database queries. 
- Escaping Input: If you must use raw input in queries use Laravel's DB::raw() method to escape the input properly. 
- Limit Database Privileges: Ensure that your database user account has the minimum necessary privileges required for your application. Avoid using accounts with full access to the database. 
- Use CSRF Protection: Cross-Site Request Forgery (CSRF) protection helps prevent malicious users from tricking authenticated users into executing unintended actions on your website. 
- Keep Laravel Updated: Keep your Laravel framework and its dependencies up to date to ensure that you have the latest security patches and features.

Example for injection

```mysql
SELECT * FROM users WHERE email = 'ahmed@bermawy.info'-- AND password = 'password';
    
Username: admin'--

`' OR '1'='1`
SELECT * FROM users WHERE username = '' OR '1'='1' AND password = '' OR '1'='1'

```

* ## What is the difference between soft delete and hard delete?

Soft delete is a way to "delete" a record without actually removing it from the database.

When a record is soft deleted, a `deleted_at` timestamp is set on the record, and the record is not returned in normal queries.

Hard delete, on the other hand, is the actual removal of the record from the database.

* ## retrieve both soft deleted and undeleted records from a database?

You can use the `withTrashed()` method to retrieve both soft deleted and undeleted records from a database.

```php
$posts = Post::withTrashed()->get();
```

* ## What is the difference between has() and whereHas() in Laravel Eloquent?

`has()` is used to filter the results based on the existence of a relationship.

`whereHas()` is used to filter the results based on the existence of a relationship and the values of the related model.

* ## What is the difference between first() and find() in Laravel Eloquent?

`first()` returns the first record that matches the query conditions.

`find()` returns a single record by its primary key.

* ## What is the N+1 issue in Laravel and how do you solve it?

The N+1 issue is a performance problem that occurs when you make N+1 queries to the database to retrieve related records.

To solve the N+1 issue in Laravel, you can use eager loading with the `with()` method.

```php
$posts = Post::with('comments')->get();
```

* ## What is the difference between Eager Loading and Lazy Loading?

Eager loading is the process of loading a model with its relationships at the time the model is queried.

Lazy loading, on the other hand, is the process of loading the relationships only when they are accessed.

example of eager loading

```php
$posts = Post::with('comments')->get();
```

example of lazy loading

```php
$post = Post::find(1);
$comments = $post->comments;
```

* ## What is the difference between Factory and Seeder?

A factory is used to define the structure of the data that will be inserted into the database.

A seeder is used to populate the database with data using the factories.

* ## What is the difference between a Repository and a Service?

A repository is a class that abstracts the data layer and provides a clean API to interact with the database.

A service is a class that encapsulates business logic and provides a clean API to interact with the application.

* ## what is throttle in Laravel?

Throttling is a way to limit the number of requests a user can make to a route within a specified time frame.

It is used to prevent abuse of the application by limiting the number of requests a user can make.

<details>

<summary>Example</summary>

```php
Route::middleware('throttle:60,1')->get('/user', function () {
    return 'Hello World';
});
```

</details>

* ## What is Event and Listener in Laravel?

Events are a way to notify other parts of the application that a certain action has occurred.

Listeners are classes that handle the events and perform the necessary actions.

example in laravel

```php



* ## What is the difference between `auth()->user()` and `Auth::user()` in Laravel?

`auth()->user()` is a helper function that returns the currently authenticated user.

`Auth::user()` is a facade that provides access to the authentication services.

* ## How to implement distributed locking in Laravel?

Distributed locking is a way to prevent multiple processes from accessing a shared resource at the same time.

In Laravel, you can use the `lockForUpdate()` method to implement distributed locking.

```php
DB::table('posts')->where('id', 1)->lockForUpdate()->get();
```

* ## How to implement builder or manager design pattern in Laravel?

<details>

<summary>Example</summary>

```php

interface ParserInterface
{
    public function parse(string $path): array;
}

class ParserManager extends Manager
{

    public function getDefaultDriver(): string
    {
        return 'json';
    }

    public function createJsonDriver(): JsonParser
    {
        return new JsonParser();
    }

    public function createCsvDriver(): CsvParser
    {
        return new CsvParser();
    }
}

class ParserServiceProvider extends ServiceProvider
{
    public function register(): void
    {
        $this->app->singleton(ParserManager::class, function ($app) {
            return new ParserManager($app);
        });

        $this->app->alias(ParserManager::class, 'parser');
    }
}

class Parser extends Facade
{
    protected static function getFacadeAccessor(): string
    {
        return 'parser';
    }
}


class CsvParser implements ParserInterface
{

    public function parse(string $path): array
    {
        $file = fopen($path, 'r');
        $rows = [];

        while (($row = fgetcsv($file)) !== false) {
            $rows[] = $row;
        }

        fclose($file);

        return $rows;
    }
}

class JsonParser implements ParserInterface
{

    public function parse(string $path): array
    {
        $json = file_get_contents($path);
        return json_decode($json, true);
    }
}

$jsonFile = storage_path('app/public/data.json');
$data = Parser::parse($jsonFile); // because json is our default driver

// to user csv driver
$csvPath = storage_path('app/public/data.csv');
$csvData = Parser::driver('csv')->parse($csvPath);

```

</details>