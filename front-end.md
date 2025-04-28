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

1. #### MonoRepo (Microfrontend) vs MultiRepo
      - Nx


1. #### Front optimization technique List
      - bundlle optimization like Tree shaking, Compression, Minification
      - remove unusiblle Import
      - Code Splitting ( Dynamic Import )
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
        -  Sends a request to fetch only the headers of a resource, without the body.

      - OPTION Method  
        -  Used to describe the communication options for a resource, like allowed methods (GET, POST, etc.).

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
        . Largest Contentful Paint (LCP)  
          - It tracks the time it takes for the largest content element (image, text, etc.) to be visible to the user.
        . First Input Delay (FID)  
          - It tracks the time from when a user first interacts with a page (like clicking a button) to when the browser starts processing that interaction.
        .  Cumulative Layout Shift (CLS)  
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
        . Custom Elements
        . Shadow DOM
        . HTML Templates
        . HTML Imports 


1. #### gzip
      - Gzip is a file compression format and utility used to reduce the size of files (such as text, HTML, JavaScript, and CSS) for faster transmission over the internet. It is widely used in web servers (like Apache or Nginx) to compress HTTP responses. and useful for Faster Load Times and Reduced Bandwidth.

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
['null','undefined', 'string', 'number', 'boolean', 'object', 'symbol', 'bigint']

1. #### Event Propagation
به معنا گسترش یا تکثیر یعنی با هر کلیک روی یک المنت همه پدر هایش هم کلیک می شود.

1. #### Event Bubbling  
وقتی روی یک `DOM` فرزند کلیک میکنیم همه  پدرها تا ریشه کلیک می شوند.

1. #### Event Capturing
دومین پارامتر `addEventListener` است که اگر `true` بشه مسیر صدا زدن ایونت ها برعکس میشه یعنی اول پدر اجرا میشه میاد به پایین

1. #### event.preventDefault()
این متد وقتی روی یک المنت اعمال میشه، مانع عملکرد ذاتی اون المنت میشه. مثلا وقتی رو یک `form` اعمال بشه، مانع ثبت شدن فرم میشه. وقتی روی یک تگ `a` اعمال بشه، باعث میشه اون لینک کار نکنه.

1. #### event.stopPropagation()
عملیات `Propagation` را متوقف می کند.

1. #### event.target vs event.currentTarget  
به طور خلاصه، event.target به عنصری اشاره می‌کند که رویداد را فعال کرده است، در حالیکه event.currentTarget به عنصری اشاره دارد که هندلر رویداد به آن اتصال دارد. 

1. #### Double NOT !!
وقتی پشت یک عملگر قرار میگیرد اون را بولین میکند

1. #### Hoisting 
معنای تحت‌الفظی کلمه Hoisting "بالا بردن" هست. توی جاوااسکریپت قبل از اینکه کدهای ما به شکل واقعی اجرا بشن، همه‌ی توابع و متغیرها به اول حوزه‌ی خودشون جابجا میشن. به همین دلیل هست که کد زیر بدون خطا کار می‌کنه:
```
smile();

function smile() {
    return ":)";
}
```

1. #### IIFE (  Immediately Invoked Function Expression )
 به تابعی گفته میشه که به محض اینکه تعریف شد، فراخوانی بشه.
 ```
 (function () { })();
 ```

1. #### apply , call, bind
 با متد  `call` , `apply` می‌تونیم یه کاری کنیم که this توی یک تابع به آبجکت دلخواه ما اشاره کنه.   
 تفاوت اونها توی نحوه‌ی استفاده از اونهاست. توی متد apply ما آرگومان‌ها رو با یک آرایه پاس می‌دادیم. اما توی call باید بصورت جدا جدا پاس بدیم. مثال سوال قبل رو در نظر بگیرید:   
 ```
 add.call(item1, 3, 2, 1);
 add.apply(item1, [3, 2, 1]);
 ```

1. #### sum in reduce 
 ```
 [1, 2, 3, 4].reduce((total, currect) => total + currect);
 ```

1. #### localStorage vs sessionStorage vs Cookies vs IndexedDB

1. #### arrow function vs traditional function

1. #### Rest vs Spread

1. #### Implicit Coercion vs Explicit Coercion
این‌ها دو روش تبدیل نوع داده توی جاوااسکریپت هستن.
- ‌‌Implicit Coercion یا ضمنی   
``` console.log(1 + '6');  ```
- Explicit Coercion یا صریح   
```  console.log(1 + parseInt('6')); ```

1. #### freeze vs seal 
این متدها برای آبجکت سراسری Object هستن. seal به معنی بستن و خاتمه‌دادن هست. متد seal مانع اضافه شدن پراپرتی جدید به آبجکت میشه. همچنین یک پراپرتی نمی‌تونه حذف بشه. فقط میشه مقدار یک پراپرتی رو ویرایش کرد. متد freeze شبیه به seal هست اما با این تفاوت که این متد اجازه ویرایش مقدار یک پراپرتی رو نمیده.