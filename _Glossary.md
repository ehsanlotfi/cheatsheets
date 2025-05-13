1. #### Static Class:
      - A `non-inheritable` class, typically used to extend `built-in classes` (e.g., String) via `extension methods`, and does not require `instantiation`;

1. #### Extension Methods:
      - Used to add methods to an existing class (like string) without modifying its source code.

1. #### Partial Class:
      - A class whose definition is split across `multiple files`, useful for `large` and `complex classes`.

1. #### Abstract Class:
      - Cannot be `instantiated` and is intended solely for `inheritance`.

1. #### Sealed Class:
      - Prevents further `inheritance`; no class can instance from it.

1. #### Reflection:
      - The process of obtaining `metadata` about objects and classes at `runtime`.

1. #### Object:
      - An instance created from a class.

1. #### Abstraction:
      - Hiding complex implementation details and showing only essential features, like a driver knowing how to accelerate without understanding the engine.

1. #### Overriding vs Overloading
      - `Overriding:` Replacing a parent class method in a derived class with a new implementation.
      - `Overloading:` Defining multiple methods with the same name but different parameters (`polymorphism`).

1. #### Abstract vs Interface:
      - Interface supports `multiple inheritance`, abstract does not.
      - Abstract can define and `implement methods`; interface can only define.
      - Abstract is used when not all methods need implementation.
      - Interface has `no constructors`.
      - Neither can be instantiated.

1. #### throw vs throw x
    - `throw` returns more information.
    
1. #### SOLID Principles
      - Single Responsibility Principle
        - Each class or module should be responsible for a single task.
      - Open-Closed Principle
        - A class should be open for extension but closed for modification.
      - Liskov Substitution Principle
        - If class A inherits from class B, objects of class A should be able to replace objects of class B without affecting the program.
      - Interface Segregation Principle
        - Interfaces should be small and specific, giving access only to the needed parts.
      - Dependency Inversion Principle
        - Higher-level classes should not depend on lower-level classes; both should depend on abstractions.

1. #### Microservices vs Monolithic
      - Microservices Advantages
        - Developer Productivity
        - Easy Deployment
      - Microservices Disadvantages
        - Complex Interactions
        - Monitoring Challenges

1. #### ACID Properties in DBMS
      - Atomicity: A transaction should be fully completed or not done at all.
      - Consistency: The database should transition from one valid state to another.
      - Isolation: Transactions should be independent of each other.
      - Durability: Changes made by a transaction must persist, even in case of failures.

1. #### Distributed Systems
      - Scaling
        - Vertical: Increasing resources on a single node.
        - Horizontal: Adding more nodes.
      - Availability
        - Ensuring services remain available even in case of failures.
        - Replication: Having backup nodes.
        - Load Balancing: Distributing load evenly.
        - Distributed Data Storage: Storing data in multiple locations.
        - Consistency Models: Defining the level of consistency among clients.
      - Latency and Performance
        - Latency: Time taken to perform an operation.
        - Performance: Overall efficiency.
        - Data Locality: Accessing data close to the processing unit.
        - Caching Strategies: Reducing data retrieval time.
      - Concurrency and Coordination
      - Monitoring and Observability
      - Resilience and Error Handling

1. #### Shallow Copy VS Deep Copy
      - Copy just reference vs. independent copy (new reference)

1. #### Mutable vs Immutable
      - Mutable: Can be changed after creation.
      - Immutable: Cannot be changed after creation.
        ```
          // Mutable Example (Object and Array)
          let obj = { name: "Alice" };
          obj.name = "Bob";  // Changed: { name: "Bob" }

          let arr = [1, 2, 3];
          arr.push(4);       // Changed: [1, 2, 3, 4]
        ```
        ```
          // Immutable Example (String and Number and ...)
          let str = "Hello";
          str[0] = "J";      // No change: "Hello" (strings are immutable)

          let num = 5;
          num = num + 1;     // Creates a new number: 6 (original 5 is unchanged)
        ```

1. #### Parallelism vs Concurrency
      - Parallelism: Two people doing different tasks at the same time without interfering with each other.
        - Example: One person draws in the living room, and another in the bedroom, both at the same time.
      - Concurrency: One person switching between tasks quickly.
        - Example: One person first draws, then reads a book, switching back and forth.

1. #### Imperative vs Declarative
      - Imperative: Focus on how to perform tasks.
      - Declarative: Focus on what to achieve.

1. #### FMP (First Meaningful Paint)
      - The first moment when the user can see the page content.

1. #### TTI (Time to Interactive)
      - The first moment when the user can interact with the page.

1. #### KISS (Keep It Simple and Stupid)
      - Write code in the simplest way possible and avoid complexity.

1. #### YANGI (You Ain't Gonna Need It)
      - Don't write code you don't need. Add code only when the need arises.

1. #### DRY (Don't Repeat Yourself)
      - Never repeat anything in your project. Keep the code clean and concise.

1. #### LoD (Law of Demeter)
      - A principle that states an object should only talk to its immediate friends, not to strangers.
      ```
      // LoD (Bad Practice)
        const car = {
        engine: {
            start: () => console.log("Engine started")
          }
        };
        car.engine.start();  // "Engine started"
      ```
      ```
      // LoD (GOOD Practice) hides internal details, promoting modularity and easier maintenance.
        const car = {
            startEngine: function() {
              this.engine.start();
            },
            engine: {
              start: () => console.log("Engine started")
            }
          };
        car.startEngine();
      ```

1. #### SOC (Separation of Concerns)
      - Dividing software into distinct sections to handle different issue.

1. #### SSL (Secure Sockets Layer) OR TLS (Transport Layer Security)
      - A security protocol used on the internet for secure communication between the browser and server.

1. #### JIT (Just-In-Time) VS AOT (Ahead-of-Time)
      - JIT compiles code at runtime, useful for development with flexibility.
      - AOT compiles code ahead of time, mostly for production environments with better performance.

1. #### Currying Technique
      - Transforming a function with multiple arguments into a sequence of functions each with a single argument.
        ```
          function logger(level, message) {
            console.log(`${level}: ${message}`);
          }

          logger('warning', 'This is a warning message');
          logger('warning', 'This is another warning message');
        ```
        ```
          function logger(level) {
            return function (message) {
              console.log(`${level}: ${message}`);
            }
          }

          const infoLog = logger('info');
          infoLog('This is an info message #1');
          infoLog('This is an info message #2');
        ```

1. #### Sharding Techniques
      - Dividing data into smaller parts and distributing them across multiple servers to improve performance.