1. #### out, ref, params:
    - `params`: Allows a method to accept a variable number of arguments.
        ```
            void PrintNumbers(params int[] numbers) {
                foreach (var number in numbers) {
                    Console.WriteLine(number);
                }
            }
            PrintNumbers(1, 2, 3, 4);  // Outputs: 1, 2, 3, 4
        ```
    - `out`: No initial value required; the method assigns it a value.
        ```
            void GetSquare(int number, out int result) {
                result = number * number;
            }

            int square;
            GetSquare(5, out square);  // square = 25
        ```
    - `ref`: Requires an initial value before being passed to the method.
        ```
            void DoubleValue(ref int number) {
                number = number * 2;
            }

            int value = 5;
            DoubleValue(ref value);  // value = 10

        ```

1. #### Encapsulation 
    - defaults is `internal`.
![image](https://github.com/ehsanlotfi/cheatsheets/assets/25532726/7b17b920-4f98-4c00-9630-ce8a8536ff69)


1. #### type of constractor
    - `Default Constructor`: Automatically called to create objects with default values, without any parameters.
        ```
            class Car {
                public string Model;
                
                // Default constructor
                public Car() {
                    Model = "Unknown";
                }
            }
            Car car = new Car();  // Model is "Unknown"
        ```
    - `Parameterized Constructor`: A constructor that takes parameters used to initialize the object's properties.
        ```
            class Car {
                public string Model;
                
                // Parameterized constructor
                public Car(string model) {
                    Model = model;
                }
            }
            Car car = new Car("Tesla");  // Model is "Tesla"
        ```
    - `Static Constructor`: A constructor used to initialize static methods or fields and is called only once when the class is loaded.
        ```
            class Car {
                public static int CarCount;

                // Static constructor
                static Car() {
                    CarCount = 0;  // This runs only once when the class is loaded
                }

                public Car() {
                    CarCount++;
                }
            }

            Car car1 = new Car();
            Car car2 = new Car();

            Console.WriteLine(Car.CarCount);  // Output: 2
        ```

1. #### ArrayList vs HashTable 
    - `ArrayList`: A data structure used to store elements in a sequence, accessed via an index, `without requiring keys`.
    - `HashTable`: A data structure that stores data as `key-value pairs`, where each element requires a unique key.

1. #### IEnumerable Vs IQueryable
    - `IEnumerable`: Used for working with `in-memory` data collections like `lists` and `arrays`. It uses `Immediate Execution` to process the data right away.
    - `IQueryable`: Used for `querying` data from external sources like `databases` (e.g., `LINQ` to `SQL`). It supports `Deferred Execution` and allows dynamic query building through Expression Trees.

1. #### Delegate VS Event 
    - `Delegate`: A `pointer` type that can hold references to one or more methods. When invoked, the method associated with it gets executed. Delegate is used to implement design patterns like `Observer` and `Callback`.
        - `Default Delegate`: A delegate that points to a specific method.
            ```
                public delegate void MyDelegate();
                public class Program
                {
                    public static void PrintMessage() 
                    {
                        Console.WriteLine("Hello, World!");
                    }

                    public static void Main(string[] args)
                    {
                        MyDelegate del = PrintMessage; // Default delegate pointing to PrintMessage method
                        del();  // Output: Hello, World!
                    }
                }
            ```
        - `Anonymous Delegate`: A delegate without a name, defined on the fly.
            ```
                public delegate void MyDelegate(int x);
                public class Program
                {
                    public static void Main(string[] args)
                    {
                        MyDelegate del = delegate(int x) { Console.WriteLine(x * 2); };  // Anonymous delegate
                        del(5);  // Output: 10
                    }
                }
            ```
        - `Multicast Delegate`: A delegate that can call multiple methods.
            ```
                public delegate void MyDelegate(int x);
                public class Program
                {
                    public static void Method1(int x) { Console.WriteLine($"Method1: {x}"); }
                    public static void Method2(int x) { Console.WriteLine($"Method2: {x}"); }

                    public static void Main(string[] args)
                    {
                        MyDelegate del = Method1;
                        del += Method2;  // Adding Method2 to the delegate (multicasting)
                        
                        del(5);  // Output: Method1: 5
                                //         Method2: 5
                    }
                }
            ```
    - `Event`: Similar to Delegate, but used to define events and notify other parts of the program when a specific action occurs. When an Event is triggered, all Delegates attached to it are executed.
        ```
            public class Program
            {
                public delegate void MyEventHandler(string message);
                public static event MyEventHandler MyEvent;

                public static void Main()
                {
                    MyEvent += (msg) => Console.WriteLine("Event says: " + msg);  // Subscribing to the event
                    MyEvent?.Invoke("Hello!");  // Triggering the event
                }
            }
        ```

1. #### const vs readonly
    - `const`: Must be assigned at the time of declaration and cannot change later.
    - `readonly`: Can be assigned either at declaration or in the constructor.

1. #### var vs dynamic 
    - `var`: The variable type is determined at compile time.
    - `dynamic`: The variable type is determined at runtime.
        ```
        var x = 10;           // Compile-time type (int)
        dynamic y = "Hello";  // Runtime type (string)

        Console.WriteLine(x);  // Output: 10
        Console.WriteLine(y);  // Output: Hello
        ```

1. #### Boxing vs unboxing
    - `Boxing`: Converting a value type to a reference type (like object).
    - `Unboxing`: Extracting the value type from the reference type.
        ```
        int x = 10;
        object obj = x;       // Boxing
        int y = (int)obj;      // Unboxing
        ```

1. #### string vs StringBuilder
    `string`: Creates a `new memory space` for each concatenation.
    `StringBuilder`: Modifies the existing memory space without creating a new one.
        ```
        string str = "Hello";
        str += " World";  // New memory allocated
        StringBuilder sb = new StringBuilder("Hello");
        sb.Append(" World");  // No new memory allocation
        ```

1. #### is vs as
    `is`: Checks if an object is of a specific type (returns true or false).
    `as`: Tries to cast an object to a specific type (returns null if the cast fails).
        ```
        object obj = "Hello";

        if (obj is string)    // Using is
            Console.WriteLine("It's a string!");

        string str = obj as string;   // Using as
        ```

1. #### Semaphore
    - Used to control access to limited resources in `concurrent programming`. In `.NET`, we use `Semaphore` and `SemaphoreSlim`.
        ```
        SemaphoreSlim semaphore = new SemaphoreSlim(2);  // Allows 2 threads

        await semaphore.WaitAsync();
        Console.WriteLine("Resource acquired");
        // Do work
        semaphore.Release();
        ```

1. #### Nullable Reference Types
    ```
    string name = null; // ERROR
    string? name = null; // OK!
    ```

1. #### Ranges and Indices
    - `Indices`: Use `^` to count from the `end` (e.g., `^1` is the last item).
    - `Ranges`: Use `..` to specify a range (e.g., `1..4` for elements 1 to 3).
        ```
        int[] numbers = { 10, 20, 30, 40, 50 };
        Console.WriteLine(numbers[^1]);       // Output: 50
        var range = numbers[1..4];            // Elements from index 1 to 3
        Console.WriteLine(string.Join(", ", range));  // Output: 20, 30, 40
        ```

1. #### Interpolated Verbatim Strings
    - `$`: Indicates interpolation (can `call varibles`).
    - `@`: Indicates a verbatim(literal) string (can `use multiline`).
    - `$@` or `@$`: Combines both for multiline and interpolated strings.
        ```
        string name = "Ehsan";
        string text = $@"
        Hello, {name}!
        Welcome to the program.
        ";
        ```

1. #### Null Coalescing Assignment (??=)
    - used  to assign a value to a variable only if that variable is `null`.
    ```
      string name = null;
      name ??= "Default Name";
      Console.WriteLine($"Name: {name}"); // Name: Default Name
    ```

1. #### Top-level statements
    - `Top-level statements` allow you to write code in a simpler, more concise way without the need to declare a `Main` method or class. This feature is available starting from `C# 9.0` and is mostly used in `console applications`.

1. #### Init-Only and Record
    - The `init-only` feature allows you to set properties only during object initialization, and these properties cannot be modified afterward.
        ```
            public record Person
            {
               public string Name { get; init; }
               public int Age { get; init; }
            }
        ```

1. #### Global Using Directives
    - With global using directives, you can define common using directives in a `single file`, and they will be automatically available across all other files in the project.