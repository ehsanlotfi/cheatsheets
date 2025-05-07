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

### Distributed Systems
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

### Imperative vs Declarative
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