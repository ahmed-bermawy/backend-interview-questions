* ## What is Object-Oriented Programming?
paradigm that relies on the concept of classes and objects. 
It is used to structure a software program into simple, reusable pieces of code.
grouping similar tasks into classes 
to use it in many places and following (DRY) principle. 

* ## What is Encapsulation?
Hiding information,
or creating a black box around objects and asking yourself what properties and methods can be accessed outside of class

* ## What is Inheritance?
A mechanism in which one class acquires the property of another class. 
For example, a child inherits parents' properties and methods.

* ## What is the difference between public, private, and protected?
`public` members are accessible from outside the class.

`private` members are only accessible from within the class.

`protected` members are accessible from within the class and any subclasses.

* ## What is the difference between abstract class and interface?
An abstract class can have both abstract and non-abstract methods, while an interface can only have abstract methods.

A class can inherit from only one abstract class, but it can implement multiple interfaces.

All the methods in the interface must be in the public visibility scope.

* ## Can the abstract class have a constructor?
Yes, abstract class can have a constructor.

* ## Can the abstract class have non-abstract methods?
Yes, abstract class can have non-abstract methods.

* ## Why do you use abstract classes?
The purpose of this is
to provide a template to inherit from and to force the inheriting class to implement the abstract methods.

When inheriting from an abstract class,
the child must define all methods marked abstract in the parent's class declaration

* ## What is Polymorphism?
Polymorphism is the ability of an object to take on many forms.

<details>

<summary>Example</summary>

```php
class Animal {
    public function makeSound() {
        return "Some sound";
    }
}

class Dog extends
Animal {
    public function makeSound() {
        return "Bark";
    }
}

class Cat extends
Animal {
    public function makeSound() {
        return "Meow";
    }
}

$animal = new Animal();
$dog = new Dog();
$cat = new Cat();

echo $animal->makeSound();  // Output: Some sound
echo $dog->makeSound();  // Output: Bark
echo $cat->makeSound();  // Output: Meow
```
</details>

* ## What are Solid Principles?
SOLID is an acronym for five design principles intended to make software designs more understandable, flexible, and maintainable.

- **Single Responsibility Principle (SRP):** A class should have one, and only one, reason to change.
- **Open/Closed Principle (OCP):** You should be able to extend a class's behavior without modifying it.
- **Liskov Substitution Principle (LSP):** Objects in a program should be replaceable with instances of their subtypes without altering the correctness of that program.
Another explanation is: parent class can be replaced with child class without breaking the application.
- **Interface Segregation Principle (ISP):** A client should never be forced to implement an interface that it doesn't use or clients shouldn't be forced to depend on methods they do not use.
- **Dependency Inversion Principle (DIP):** High-level modules should not depend on low-level modules. Both should depend on abstractions. Abstractions should not depend on details. Details should depend on abstractions. 
Another explanation is: Depend on abstraction, not on concrete.

* ## What is DRY?
**Don't Repeat Yourself (DRY):** is a principle of software development aimed at reducing repetition of software patterns, to avoid redundancy.

* ## What is YAGNI?
**You Aren't Gonna Need It (YAGNI):** is a principle that states a programmer should not add functionality until deemed necessary.

* ## What is KISS?
**Keep It Simple, Stupid (KISS):** Most systems work best if they are kept simple rather than made complicated.

* ## what is the difference between composition and inheritance?
Composition and inheritance are two fundamental concepts in object-oriented programming
that define relationships between classes.
Here's a brief overview of each:

**Inheritance:**
- Inheritance is a mechanism where a new class (subclass or derived class) is created based on an existing class
(superclass or base class).
- The subclass inherits attributes and behaviors (methods) from the superclass.
- It promotes code reusability and establishes an "is-a" relationship between classes.
- Example: Dog and Cat classes can inherit from a Animal superclass because they are types of animals.

**Composition:**
- Composition is a concept where a class is composed of one or more objects of other classes.
The composed objects are typically referred to as "components" or "parts."
- Unlike inheritance,
composition does not inherit behavior but rather includes behavior from other classes by creating instances of them.
- It promotes code reusability and establishes a "has-a" relationship between classes.
- Example: A Car class may have an Engine class and Wheel class as its components.

In summary, inheritance is about "is-a" relationships and promotes code reuse by deriving one class from another,
while composition is about "has-a" relationships
In general,

composition is often preferred over inheritance because it promotes looser coupling between classes
and allows for more flexible and maintainable code.
However, inheritance can still be useful in situations where there is a clear and natural hierarchy among classes

* ## what is the difference between a docker and a virtual machine?
Docker and virtual machines (VMs) are both used to deploy and run applications in isolated environments.

Here are some key differences between Docker and virtual machines:

**Architecture:**
- VMs: VMs run on a hypervisor, which abstracts physical hardware and allows multiple VMs to run on a single physical machine. Each VM includes a complete operating system, virtualized hardware, and a full set of binaries required to run applications.
- Docker: Docker uses containerization to package applications and their dependencies into isolated containers. Containers share the host machine's kernel and run as isolated processes, providing lightweight, portable, and efficient application deployment.

**Resource Efficiency:**
- VMs: VMs are heavier in terms of resource usage because they require a full operating system to be loaded for each instance, including memory, disk space, and CPU.
- Docker: Docker containers are lightweight, as they share the host machine's kernel and only require resources for the application and its dependencies. This makes Docker more resource-efficient than VMs.

**Isolation:**
- VMs: VMs provide strong isolation, as each VM has its own virtualized hardware and runs its own operating system, making them suitable for running multiple different operating systems on the same physical machine.
- Docker: Docker containers are less isolated than VMs because they share the host machine's kernel. However, they provide sufficient isolation for most applications and offer better performance and efficiency.

**Portability:**
- VMs: VMs are less portable because they require a hypervisor to run, which may not be available on all systems. Moving VMs between different hypervisors or cloud providers can be complex.
- Docker: Docker containers are highly portable, as they include all dependencies and configurations required to run the application. Containers can be easily moved between different environments that support Docker.

**Startup Time:**
- VMs: VMs typically have longer startup times because they need to boot a full operating system.
- Docker: Docker containers have faster startup times because they do not need to boot an entire operating system, only the application and its dependencies.

* ## What is PWA?
Progressive Web Apps
converting your website into a mobile app that can be deployed as an app and can be used as an offline service

* ## What is final keyword in OOB?
The `final` keyword is used to restrict the inheritance of a class or the overriding of a method.

When a class is declared as `final`, it cannot be subclassed or extended by other classes.

When a method is declared as `final`, it cannot be overridden by subclasses.

* ## What is dependency injection?
Dependency injection is a design pattern in which a class receives its dependencies from external sources rather than creating them itself.
This pattern promotes loose coupling between components, making the code more maintainable, testable, and reusable

* ## What is Active record?
An active record pattern is an approach to accessing data in a database.
A database table is wrapped into a class.
an object instance is tied to a single row in the table.
After the creation of an object, a new row is added to the table upon the save method.
Any object loaded gets its information from the database.
When an object is updated, the corresponding row in the table is also updated.
The wrapper class implements accessor methods

more about Active record

<a target="_blank" href="https://www.youtube.com/watch?v=ZRdgVuIppYQ/">Active record</a>

* ## What is Data mapper?
A Data Mapper is a Data Access Layer that performs bidirectional data transfer between a persistent data store (often a relational database) and an in-memory data representation (the domain layer).
The goal of the pattern is to keep the in-memory representation and the persistent data store independent of each other and the data mapper itself

* ## What is a Decorator design pattern?
is a structural pattern
that allows adding new behaviors to objects dynamically by placing them inside particular wrapper objects,
called decorators.

<details>

<summary>Example</summary>

```php
interface Coffee {
    public function cost();
}

class SimpleCoffee implements Coffee {
    public function cost() {
        return 10;
    }
}

class MilkCoffee implements Coffee {
    protected $coffee;

    public function __construct(Coffee $coffee) {
        $this->coffee = $coffee;
    }

    public function cost() {
        return $this->coffee->cost() + 5;
    }
}

class WhipCoffee implements Coffee {
    protected $coffee;

    public function __construct(Coffee $coffee) {
        $this->coffee = $coffee;
    }

    public function cost() {
        return $this->coffee->cost() + 2;
    }
}

$coffee = new SimpleCoffee();
echo $coffee->cost();  // Output: 10

$coffee = new MilkCoffee($coffee);
echo $coffee->cost();  // Output: 15

$coffee = new WhipCoffee($coffee);
echo $coffee->cost();  // Output: 17
```

</details>


* ## Memcached VS Redis?

Memcached and Redis are both popular in-memory caching systems, but they have some differences in terms of features, performance, and use cases.

**Memcached:**

- **Data Structures:** Memcached is a simple key-value store with no support for complex data structures.
- **Data Persistence:** Memcached does not support data persistence by default, so data is lost when the server restarts.
- **Replication:** Memcached does not support built-in replication.
- **Use Cases:** Memcached is well-suited for simple caching needs where high-performance and simplicity are more important than advanced features.

**Redis:**

- **Data Structures:** Redis supports various data structures such as strings, lists, sets, sorted sets, and hashes, making it more versatile for different use cases.
- **Data Persistence:** Redis supports various persistence options, including snapshots and append-only files (AOF), allowing data to be saved to disk.
- **Replication:** Redis supports master-slave replication, allowing for data redundancy and high availability.
- **Advanced Features:** Redis includes advanced features such as transactions, pub/sub messaging, and Lua scripting, making it suitable for a wide range of use cases beyond simple caching.
- **Use Cases:** Redis is suitable for use cases that require more than simple key-value caching, such as real-time analytics, message queuing, and leaderboards.

* ## How to scale a web application?
Scaling a web application involves increasing its capacity to handle more traffic, users, and data without sacrificing performance or reliability.

Here are some common strategies for scaling a web application:

**Vertical Scaling:**
- Vertical scaling involves increasing the capacity of a single server by adding more resources, such as CPU, memory, or storage.
- This approach is relatively simple but has limitations in terms of scalability and cost-effectiveness.

**Horizontal Scaling:**

- Horizontal scaling involves adding more servers to distribute the load across multiple machines.
- This approach is more scalable and cost-effective than vertical scaling but requires additional infrastructure and configuration.
- Load Balancing: Load balancing distributes incoming traffic across multiple servers to ensure optimal performance and availability.
- Caching: Caching frequently accessed data or content can reduce the load on the database and improve response times.
- Database Sharding: Database sharding involves partitioning a database into smaller, more manageable pieces to distribute the load across multiple servers.
- Content Delivery Networks (CDNs): CDNs cache static content on servers located closer to users, reducing latency and improving performance.
- Microservices Architecture: Microservices break down an application into smaller, independent services that can be deployed, scaled, and maintained separately.
- Auto-Scaling: Auto-scaling automatically adjusts the number of servers based on traffic patterns, ensuring optimal performance and cost efficiency.

* ## What is the difference between a monolithic and microservices architecture?
Monolithic and microservices architectures are two different approaches to designing and building software applications.

**Monolithic Architecture:**

- In a monolithic architecture, the entire application is built as a single, self-contained unit.
- All components of the application, such as the user interface, business logic, and data access layer, are tightly coupled and run as a single process.
- Monolithic applications are typically easier to develop, test, and deploy but can become complex and difficult to maintain as they grow in size and complexity.
- Scaling a monolithic application involves scaling the entire application, which can be inefficient and costly.

**Microservices Architecture:**

- In a microservices architecture, the application is broken down into smaller, independent services that communicate with each other through APIs.
- Each service is responsible for a specific function or feature of the application and can be developed, deployed, and scaled independently.
- Microservices architectures promote modularity, flexibility, and scalability but can introduce complexity in terms of service communication, data consistency, and deployment orchestration.
- Scaling a microservices application involves scaling individual services based on demand, allowing for more efficient resource utilization and cost management.
- Microservices architectures are well-suited for large, complex applications with diverse requirements and technologies but require careful design and management to be successful.


* ## what is use of API Gateway?
An API Gateway is a server that acts as an API front-end,
receiving API requests, enforcing throttling and security policies,
passing requests to the back-end service, and then passing the response back to the requester.

like a reverse proxy, accepting a request and routing it to the appropriate service.

API Gateway can provide functionality such as authentication,
rate limiting, caching, request and response transformations,
and logging and monitoring and caching, and load balancing, and security,
and API versioning, and error handling, and routing.

technologies used in API Gateway include Amazon API Gateway, Apigee,
NGINX, Azure API Management.

* ## What is Swagger?
Swagger is a set of open-source tools built around the OpenAPI Specification that can help you design, build, document,
and consume RESTful web services.

* ## What is the different between basic authentication and bearer token?
Basic Authentication sends HTTP requests with the Authorization header
that contains the word Basic followed by a space and a base64-encoded string username:password.

    --header 'Authorization: Basic d2ViYXBpOkR3QSFoZWZHUDIx' 

Bearer Token sends HTTP requests with the Authorization header
that contains the word Bearer followed by a space and a token.

the token can be decoded to get the user information.

    --header 'Authorization: Bearer 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'

* ## What is the difference cookies and local storage?
Cookies and local storage are two ways to store data in a web browser, but they have some key differences:

**Cookies:**

- Small pieces of data stored in the browser that are sent with every HTTP request to the server, which can impact performance and increase network traffic.
- It Has a size limit of 4KB and can store up to 20 cookies per domain.
- It Can be set with an expiration date and can be used for session management.
- Vulnerable to cross-site scripting (XSS) attacks and can be accessed by both the server and client-side scripts.
- Is accessible via the `document.cookie` object in JavaScript and can be used to store and retrieve data using key-value pairs.

**Local Storage:**

- Feature of modern web browsers that allows data to be stored locally on the user's device.
- Has a size limit of 5MB per domain and is not sent with HTTP requests to the server.
- Persistent and remains stored even after the browser is closed and reopened.
- Used for storing user preferences, settings, and other data that does not need to be sent to the server.
- Not vulnerable to XSS attacks and can only be accessed by client-side scripts running in the same domain.
- More secure than cookies but may not be suitable for storing sensitive data.
- Is accessible via the `localStorage` object in JavaScript and can be used to store and retrieve data using key-value pairs.


* ## What is a Singleton and why it is not recommended?
The Singleton design pattern is a creation pattern
that ensures a class has only one instance and provides a global point of access to that instance.

it is considered an anti-pattern due to the following reasons:

**Global State:**
- Singletons introduce global state into an application, making it harder to manage and test.
- Global state can lead to tight coupling between components and make it difficult to reason about the flow of data and dependencies.
- Difficult to Test: Singletons can make unit testing more challenging because they introduce hidden dependencies and shared state.
- Singletons can make it difficult to isolate and test individual components in isolation.
- Violates Single Responsibility Principle: Singletons can violate the Single Responsibility Principle by combining the responsibilities of creating an instance and managing its lifecycle.

**Concurrency Issues:**
- Singletons can introduce concurrency issues in multi-threaded environments.

**Difficult to Extend:**
- Singletons can be difficult to extend or modify because they rely on static methods and state.
- Changing the behavior of a Singleton can require modifying the class itself, which can lead to code changes in multiple places.
- Difficult to Mock: Singletons can be difficult to mock or replace with test doubles in unit tests.

* ## What is key-clock and why it is used?
Keycloak is an open-source identity and access management solution that provides features such as single sign-on,
social login, and centralized user management.

Keycloak can be used to secure applications and services by providing authentication,
authorization, and user management capabilities.

* ## What is identity server and why it is used?
IdentityServer is an open-source identity and access management solution that provides features such as single sign-on,
social login, and centralized user management.

IdentityServer can be used to secure applications and services by providing authentication, authorization,

* ## What is a Repository design pattern?
The Repository design pattern is a design pattern
that separates the data access logic from the business logic in an application.

The Repository acts as an intermediary between the data source and the business logic,
providing a clean and consistent interface for accessing data using dependency injection.

The Repository pattern provides a way to centralize data access logic and abstract the underlying data store,
making it easier to test and maintain the application.

additional benefits

**Flexibility**: You can easily change the data source (for example, switch from a database to an external API) without affecting the rest of the application.

**Reusability**: Repositories allow you to reuse logic in multiple parts of your app, reducing code duplication.

**Testability**: It’s easier to test, as you can mock or replace the repository during testing.

**Organization & Clarity**: Repositories keep your code clean and structured, making it easier to understand and maintain.


<details>

<summary>Example</summary>

```php
interface UserRepositoryInterface {
    public function findById($id);
    public function findByEmail($email);
    public function save(User $user);
    public function delete(User $user);
}

class UserRepository implements UserRepositoryInterface {
    public function findById($id) {
        // Implementation
    }

    public function findByEmail($email) {
        // Implementation
    }

    public function save(User $user) {
        // Implementation
    }

    public function delete(User $user) {
        // Implementation
    }
}

class UserService
{
    protected $userRepository;

    public function __construct(UserRepositoryInterface $userRepository)
    {
        $this->userRepository = $userRepository;
    }

    public function getUserById($id)
    {
        return $this->userRepository->findById($id);
    }

    public function saveUser(User $user)
    {
        return $this->userRepository->save($user);
    }
}
```

</details>



* ## What is a Factory method design pattern?
The Factory Method design pattern is a creational pattern
that provides an interface for creating objects in a superclass

but it allows subclasses to alter the type of objects that will be created.

It promotes loose coupling between the creator and the product,

allowing the creator to delegate the responsibility of creating objects to subclasses.

<details>

<summary>Example</summary>

```php
interface Vehicle {
    public function drive();
}

class Car implements Vehicle {
    public function drive() {
        return 'Driving a car';
    }
}

class Truck implements Vehicle {
    public function drive() {
        return 'Driving a truck';
    }
}

interface VehicleFactory {
    public function createVehicle();
}

class CarFactory implements VehicleFactory {
    public function createVehicle() {
        return new Car();
    }
}

class TruckFactory implements VehicleFactory {
    public function createVehicle() {
        return new Truck();
    }
}

$carFactory = new CarFactory();

$car = $carFactory->createVehicle();
echo $car->drive();  // Output: Driving a car

$truckFactory = new TruckFactory();

$truck = $truckFactory->createVehicle();

echo $truck->drive();  // Output: Driving a truck
```

</details>

* ## What is the difference between Hashing and Encryption?

**Hashing:**

- Hashing is a one-way process that converts input data into a fixed-size string of bytes.
- Hash functions are deterministic, meaning the same input will always produce the same output.
- Hashing is used to verify data integrity, generate checksums, and store passwords securely.
- like md5, sha1, sha256, sha512

**Encryption:**

- Encryption is a two-way process that converts input data into a ciphertext that can be decrypted back into the original data.
- Encryption uses keys to encrypt and decrypt data, providing confidentiality and privacy.
- Encryption is used to protect sensitive data, secure communications, and prevent unauthorized access.
- like AES, DES, RSA

* ## What is a Strategy design pattern?

The Strategy design pattern is a behavioral pattern

that defines a family of algorithms, encapsulates each algorithm, and makes them interchangeable.

* ## How dependency container works?

A dependency container is a design pattern that allows objects to be created and managed by an external container.

The container is responsible for instantiating objects, managing their dependencies, and providing them to other objects that need them.

The container uses a configuration file or code to define the relationships between objects and their dependencies.

When an object requests a dependency from the container,
the container resolves the dependency and provides it to the object.

Dependency containers promote loose coupling between components,
improve code reusability, and make it easier to test and maintain applications.

* ## How many type of debenency injection we have?

There are three types of dependency injection:

**Constructor Injection:**

- Dependencies are provided to a class through its constructor.
- Constructor injection ensures that all dependencies are provided when an object is created.
- Constructor injection promotes immutability and makes dependencies explicit.

**Setter Injection:**

- Dependencies are provided to a class through setter methods.
- Setter injection allows dependencies to be set or changed after an object is created.
- Setter injection is more flexible than constructor injection but can lead to mutable objects.

**Method Injection:**

- Dependencies are provided to a class through method parameters.
- Method injection allows dependencies to be passed to specific methods as needed.
- Method injection is useful for providing dependencies to specific methods without affecting the class's state.

* ## How do we decide that a particular domain problem should be converted into microservices?

Deciding whether to convert a particular domain problem into microservices involves considering several factors:

**Scalability:**

- Scaled independently, allowing specific services to be scaled based on demand.

**Complexity:**

- Manage complexity by breaking down a large application into smaller, more manageable services.

**Isolation:**

- Isolation between services, allowing failures in one service to be contained and not affect other services.

**Technology Stack:**

- Allow different services to be developed using different technologies and frameworks.

**Deployment Flexibility:**

- Deployed independently, allowing services to be updated and deployed without affecting other services.

**Performance:**

- Improve performance by allowing services to be optimized and scaled independently.

**Data Management:**

- Manage data by allowing each service to have its own data store or database.

**Cost:**

- Increase infrastructure and operational costs due to the need for additional services and infrastructure.

* ## Facade Design Pattern:

The Facade design pattern is a structural pattern that provides a simplified interface to a complex subsystem.

pros:
* Simplifies usage of complex systems.
* Reduces dependencies between client code and subsystems.
* Encapsulates changes — if subsystems change, client code stays the same.

cons:
* Hides functionality — advanced users may lose flexibility.
* It Can become a god class if it grows too large.
* Adds an extra layer, which may slightly affect performance in large systems.


* ## What is service oriented architecture (SOA)?
Service-Oriented Architecture (SOA) is a design pattern
that structures an application as a collection of loosely coupled services.
Each service represents a specific business function and communicates with other services through well-defined interfaces and protocols.
SOA promotes reusability, scalability, and flexibility by allowing services to be developed, deployed, and maintained independently.

example of SOA: 
using services classes in project like authentication service, payment service, notification service, etc.





