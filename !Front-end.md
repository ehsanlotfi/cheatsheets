1. #### Hydration
  - `Literal meaning` Giving water to a person who has lost a lot of water from their body.
  - Hydration is the process of making a server-rendered `HTML` page interactive by attaching `JavaScript`.

1. #### llms.txt 
  - Is a simple text file at your website’s root that helps AI models understand your site’s key content. 

1. #### Service Worker
     - A Service Worker is a special script that runs in the background of a web app. It helps with `offline access`, `caching`, `faster loading`, sending `push notifications` and `PWA`.

1. #### Web Workers
     - Web Workers let you run JavaScript code in `parallel`, even though JavaScript is normally single-threaded. They are great for background tasks like processing GPS data, handling sensor inputs, and monitoring real-time events without slowing down the main page

1. #### Service Worker VS Web Workers
      - Web Workers run code in the background for heavy tasks, while Service Workers handle network requests, caching, and push notifications. Both cannot directly access the DOM.

1. #### build tools
      - webpack
      - gulp 
      - grunt

1. #### Event Loop
      - The Event Loop in JavaScript is a mechanism that allows `asynchronous` code—like `setTimeout` or `fetch` run without blocking the main thread. Since JavaScript is `single-threaded`, the Event Loop waits until the `call stack` is empty, then takes functions from the `task queue` and pushes them to the stack for execution. This makes it possible to handle multiple tasks seemingly at the same time

1. #### Web APIs
      - Web APIs are built-in browser interfaces that allow JavaScript to interact with the browser, system, or external services.
          - `DOM API` – Interact with HTML elements (document.querySelector, element.innerText).
          - `BOM API` – Control browser window and environment (window, navigator).
          - `Fetch &` Network API – Handle HTTP requests (fetch, XMLHttpRequest, WebSocket).
          - `Storage API` – Store data in browser (localStorage, sessionStorage, IndexedDB).
          - `Multimedia API` – Work with audio/video (MediaDevices, AudioContext).
          - `Graphics API` – Draw graphics and animations (Canvas, WebGL).
          - `Device & Sensor API` – Access hardware features (Geolocation, DeviceOrientation).
          - `Clipboard & Drag-and-Drop API` – Handle user copy-paste and drag actions.
          - `Notifications & Background API` – Show notifications, sync in background (Notification, Service Worker).
          - `Performance & Timing API` – Measure performance and handle animation frames.

1. #### MonoRepo  vs Microfrontend
      - `MonoRepo` is a version control strategy where multiple projects (often related or interdependent) are stored in a `single repository`.
        - [Nx](https://nx.dev/)
        - [Turborepo](https://turborepo.com)
        - [Lerna](https://lerna.js.org/)
        - [Bazel](https://bazel.build/)
        - [Rush](https://rushjs.io/)

      - `Microfrontend` is an architectural approach where a frontend application is divided into smaller, independently developed, deployed, and maintained pieces.
        - [Module Federation (Webpack)](https://webpack.js.org/concepts/module-federation/)
        - [Single-SPA](https://single-spa.js.org/)
        - [Qiankun](https://qiankun.umijs.org/)
        - [Piral](https://piral.io/)

1. #### Front optimization technique List
      - bundlle optimization like Tree shaking, Compression, Minification
      - remove unusiblle Import
      - Code Splitting ( Dynamic Import )
        - It is a feature supported by bundlers like webpack and browserify, which can create different bundles that can be dynamically   loaded at runtime.
      - Lazy Loading
      - Conditional components loading
      - Handle API requests ( AbortController )

1. #### AbortController
     - Means you can start a request and cancel it if needed
      ```
      const controller = new AbortController();
      fetch('https://example.com/api/data', { signal: controller.signal })
        .then(response => response.json())
        .then(data => console.log(data))
        .catch(error => console.error(error));
      controller.abort();
      ```

1. #### Non-null Assertion
       - This operator tells TypeScript that the value is definitely not null, even without a check.
      ```
        // use the '!' character   at the end of the phrase
        const test = model.user.name!;
      ```

1. #### Shallow Rendering
      -  it's a test technique that tests a component without rendering its child components.

1. #### Polyfill 
      -  A piece of code that adds missing javascript new features (like Ecmascript new features) to older browsers.

1. #### Utility Types in TypeScript 
      - `Partial<Type>`
        -  Makes all properties of a type optional.
      - `Required<Type>`
        -  Makes all properties of a type required.
      - `Readonly<Type>`
        -  Makes all properties of a type readonly.
      - `Record<Keys, Type>`
        -  Creates an object type with specific keys and all values of a specific type.
          ```
          type Names = 'John' | 'Mario' | 'Emily';
          type PersonInfo = { age: number, hobbies: string };

          type Persons = Record<Names, PersonInfo>;

          const persons: Persons = {
            'Emily': { age: 4, hobbies: 'Sleep' },
            'John':  { age: 5, hobbies: 'Video Games' },
            'Mario': { age: 3, hobbies: 'Space' },
          };
          ```
      - `Pick<Type, Keys>`
        -  Creates a new type by selecting specific properties from another type. 
          ```
          type Person = {
            name: string;
            age: number;
            hobbies: string;
            status: string;
            created_at: string;
          }

          type MiniPerson = Pick<Person, "name" | "age">;

          const john: MiniPerson = {
              name: 'John',
              age: 4,
          }
          ```
      - `Omit<Type, Keys>`
        -  Creates a new type by removing specific properties from another type.


1. #### RESTful API
      - HEAD Method  
        - Same as `GET`, but only returns headers, not the body.
        - Used to check if a resource exists or to know its size/type without downloading it.

      - OPTION Method  
        -  Returns which HTTP methods are allowed for a resource.
        - Often used for CORS (browsers check permissions before the real request).

1. #### picture Tag
      -  Used to specify multiple image sources for different screen sizes or resolutions. It allows responsive images.

        ```
          <picture>
            <source media="(min-width: 900px)" srcset="img-large.jpg">
            <source media="(min-width: 600px)" srcset="img-medium.jpg">
            <img src="img-small.jpg">
          </picture>
        ```

1. #### what is d.ts in TypeScript
      - A declaration file that defines types, interfaces, and modules for external libraries, allowing TypeScript to understand their structure without the actual implementation.


1. #### Map vs WeakMap
      - Map:
          Stores key-value pairs where both keys and values can be any type. Keys are kept in memory, even if they are no longer used.

      - WeakMap:
          Stores key-value pairs where keys must be objects. The keys are garbage collected when there are no other references to them, preventing memory leaks.
      ```
        let map = new Map();
        let weakMap = new WeakMap();

        let objKey = {name: 'John'};

        map.set(objKey, 'Map Value');
        weakMap.set(objKey, 'WeakMap Value');

        console.log(map.get(objKey));  // Output: 'Map Value'
        console.log(weakMap.get(objKey));  // Output: 'WeakMap Value'

        // Dereference the object
        objKey = null;

        console.log(map.get(objKey));  // Output: 'Map Value' (Map still holds the key)
        console.log(weakMap.get(objKey));  // Output: undefined (WeakMap removes the key)

      ```

1. #### Closure
      - A closure is a function that retains access to variables from its lexical scope, even after the outer function has finished executing. This means that the inner function "remembers" the environment in which it was created,  including any variables from the outer function.
        ```
        function outer() {
            let counter = 0;  // `counter` is in the outer function's scope
            
            return function inner() {  
              counter++;  // The `inner` function still has access to `counter`
              console.log(counter);
            };
          }

          const increment = outer();  // `increment` is a closure
          increment();  // Output: 1
          increment();  // Output: 2
        ```

1. #### preload vs prefetch
        - Both of them are for downloading resources before they are needed.
        - Preload is for resources needed right away, while Prefetch is for resources that will be used later.
        - Preload blocks the page rendering to fetch the resource, while Prefetch works in the background to optimize future page loads.
          ```
          <link rel="preload" href="/font.woff" as="font" />
          <link rel="prefetch" href="/prism.js" as="script" />
          ```

1. #### Core Web Vitals 
      - A set of performance metrics used by Google to measure the user experience of a website
        - Largest Contentful Paint (LCP)  
          - It tracks the time it takes for the largest content element (image, text, etc.) to be visible to the user.
        - First Input Delay (FID)  
          - It tracks the time from when a user first interacts with a page (like clicking a button) to when the browser starts processing that interaction.
        -  Cumulative Layout Shift (CLS)  
          -  It tracks how much the page layout shifts during loading, causing unexpected movement of content.

1. #### CORS ( Cross-Origin Resource Sharing )
      - A security feature implemented by web browsers to restrict how web pages can request resources from domains other than their own.


1. #### Call Stack  
      - A tool in the browser or JavaScript that helps us track function calls.

1. #### prototype
      - A prototype is an object that provides shared properties and methods for other objects, enabling inheritance. like `length`

1. #### Pseudo-elements vs Pseudo-classes
      ```
      // Pseudo-elements show in DOM
      a::after { }, a::before { }


      // Pseudo-classes not showing in DOM
      a:hover { }, a:focus { } , ...
      ```

1. #### for...in
      - It iterates over object and have high order time due to prototypes.

1. #### Web Components
      - Advantages  
        Reusable, Encapsulated
      - terms
        - Custom Elements
        - Shadow DOM
        - HTML Templates
        - HTML Imports 


1. #### gzip
      - `Gzip` is a file compression format and utility used to reduce the size of files (such as text, HTML, JavaScript, and CSS) for faster transmission over the internet. It is widely used in web servers (like Apache or Nginx) to compress HTTP responses. and useful for Faster Load Times and Reduced Bandwidth.

1. #### void vs never in typescript
        - `void` used for functions that don’t return anything.
        - `never` used for functions that never return (for example, they throw an error or enter an infinite loop).

        ```
            function logMessage(message: string): void {
              console.log(message);
            }

            function throwError(message: string): never {
              throw new Error(message);
            }
        ```

1. #### JavaScript types  
      - 'null', 'undefined', 'string', 'number', 'boolean', 'object', 'symbol', 'bigint'

1. #### Event Propagation (Capturing, Bubbling)
      - Event Propagation is the process of an event traveling through the DOM, including both capturing (top to target) and bubbling (target to top); you choose the phase using addEventListener's third argument (true for capture,  false for bubble).
      - `event.stopPropagation()`
        - prevents the event from bubbling up or capturing down the DOM tree.

1. #### event.preventDefault()
      - event.preventDefault() stops the default action of an element, often used with forms and links (<a> tags).

1. #### event.target vs event.currentTarget  
      - `event.target` is the element that actually triggered the event.
      - `event.currentTarget` is the element that the event listener is attached to.
      ```
        parent.addEventListener('click', function(event) {
          console.log('target:', event.target);
          console.log('currentTarget:', event.currentTarget);
        });
      ```
      - If you click a child inside parent, event.target will be the child, and event.currentTarget will be parent. Want a visual or analogy to better understand the difference?

1. #### Double NOT !!
      - is a common trick to convert any value to a boolean.

1. #### Hoisting 
      - Hoisting is JavaScript's behavior of moving declarations (not initializations) to the top of their scope before code execution.
        ```
          smile();

          function smile() {
              return ":)";
          }
        ```

1. #### Type of scopes
        - `Global Scope`: Accessible everywhere.
        - `Function Scope`: Accessible only within a function.
        - `Block Scope`: Accessible only within a block (`if block`, `for(loop) block`, ...).
        - `Module Scope`: Accessible within a module unless exported.
        - `Lexical Scope`: Inner functions can access variables from their parent scope.
          ```
          function outerFunction() {
              let outerVar = "I am from outer";
              function innerFunction() {
                  console.log(outerVar); // Accessible due to lexical scope
              }
              return innerFunction;
          }
          ```

1. #### TDZ (Temporal Dead Zone)
        - `TDZ` is the time before a `let` or `const` variable is declared, where trying to use it gives a `ReferenceError`. With `var`, this doesn't happen because it's `hoisted` and set to `undefined`.
        ```
          console.log(x); // ❌ ReferenceError: Cannot access 'x' before initialization
          let x = 5;
        ```

1. #### Debounce vs Throttle
      - `Debounce` waits for a specific time after the last event, and only runs if no new event happens during that time (e.g., during search typing).
      - `Throttle` ensures a function runs once during a fixed time period, no matter how many times the event occurs (e.g., scroll, resize, Mousemove).

1. #### apply , call, bind
      - `call()` and `apply()` invoke the function immediately but differ in how arguments are passed.
         ``` func.call(thisArg, arg1, arg2, ...) ```
         ``` func.apply(thisArg, [arg1, arg2, ...]) ```
      - `bind()` creates a new function with a bound this, and you call it later.
        ```
          const greetAlice = greet.bind(null, "Alice");
          greetAlice();
        ```

1. #### Reduce 
        ```
        [1, 2, 3, 4].reduce((total, currect) => total + currect);
        ```

1. #### localStorage, sessionStorage, Cookies, IndexedDB, webSQL
    - They differ in data size and lifetime and data type.

1. #### Types of Functions
      - Regular Functions.
        - ``` function greet() { console.log("Hello!"); } ```
      - Arrow Functions.
        - ``` const greet = () => { console.log("Hello!"); } ```
      - Anonymous Functions
        - Functions without a name, often used in callbacks or as arguments to other functions.
        ``` setTimeout(function() { console.log("Hello!"); }, 1000); ```
      - IIFE (Immediately Invoked Function Expressions)
        -  is a function that runs immediately after it's defined.
        ``` (function () { })(); ```

1. #### Rest vs Spread
      - `rest` Collects multiple elements into one array or object.
      ```
        function sum(...numbers) {
          return numbers.reduce((a, b) => a + b, 0);
        }
      ```
      - `Spread` Expands (spreads out) an array or object into individual elements.
      ```
        const arr = [1, 2, 3];
        console.log(...arr); // 1 2 3
      ```
1. #### Implicit Coercion vs Explicit Coercion
      - two ways of typecasting in JavaScript.
      - ‌‌Implicit Coercion
      ``` console.log(1 + '6');  ```
      - Explicit Coercion
      ```  console.log(1 + parseInt('6')); ```

1. #### freeze vs seal 
      - `Object.seal()`
        - Prevents adding or removing properties, but you can still modify existing ones.
      - `Object.freeze()`
        - Prevents adding, removing, and modifying properties.

1. #### HMR (Hot Module Replacement ) vs Hot reload
    - `HMR (Hot Module Replacement):` Only the changed part of the app is updated without a full reload, and the state is preserved.
    - `Hot Reload:` The whole page is reloaded, and the app's state may be lost.