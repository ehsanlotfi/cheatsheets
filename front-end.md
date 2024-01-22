#### کاربرد های سرویس ورکر
- مدیریت شبکه
-  کش‌سازی و ذخیره‌سازی پیش‌فرض
-  نمایش اطلاعات کش شده آفلاین در صورت نبودن اینترنت
-  پوش نوتیفیکشن و اعلان در صورتی که مرورگر بسته باشد
#### وب ورکر
-  پردازش موازی: اگرچه جاوا اسکریپت به طور اصلی تک نخی است، اما با استفاده از ورکرهای وب، می‌توانید به صورت موازی کد را اجرا کنید و عملکرد برنامه‌های خود را بهبود دهید.
-  پردازش داده‌های ورودی در پس زمینه: برای مثال، پردازش داده‌های ورودی GPS و دستگاه‌های حسگر، مانیتورینگ رخدادها و وقایع در زمان واقعی و سایر ورودی‌هایی از طریق پیام‌رسان‌ها.

#### تفاوت وب ورکر و سرویس ورکر
به طور خلاصه، وب ورکرها برای **اجرای موازی** کدها در پس زمینه صفحه در حالیکه سرویس ورکرها برای **مدیریت شبکه**، **کش**، **پوش نوتیفیکیشن** و مدیریت درخواست‌های شبکه در تحولات صفحه مناسب هستند. هر دو دسترسی به دام ندارند.

#### build tools
- webpack
- gulp 
- grunt

#### MonoRepo (Microfrontend) vs MultiRepo
- Nx


### Front optimization technique List
- bundlle optimization like Tree shaking, Compression, Minification
- remove unusiblle Import
- Code Splitting ( Dynamic Import )
- Lazy Loading
- Conditional components loading
- Handle API requests ( AbortController )

##### AbortController
 یک ویژگی در وب API های مدرن است که به توسعه دهندگان وب این امکان را می دهد که درخواست های شبکه را لغو کنند. 
```
// ساخت یک نمونه از AbortController
const controller = new AbortController();

// ایجاد یک درخواست شبکه با استفاده از AbortController
fetch('https://example.com/api/data', { signal: controller.signal })
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error(error));

// لغو درخواست با فراخوانی متد abort روی کنترلر
controller.abort();

```

### Maintainable 
برنامه‌ای هست که به راحتی و در هر زمانی می‌تونیم اون رو ویرایش کنیم، باگ‌های اون رو برطرف کنیم، توسعه بدیم و به اون توسعه‌دهنده‌های دیگه‌ای اضافه کنیم. 

#### Non-null Assertion
- این عملگر به تایپ‌اسکریپت میگه که ما مطمئن هستیم این عبارت Null نیست و لطفاً توی ادامه Null بودن اون رو بررسی نکن
```
// use the '!' character   at the end of the phrase
const test = model.user.name!;
```

#### Shallow Rendering
یک تکنیک تست‌نویسی هست که بیشتر توی فریم‌ورک‌های Component-Based مثل ویو و ری‌اکت دیده میشه
وقتی می‌خوایم یک کامپوننت رو با تکنیک Shallow Rendering تست کنیم، هنگام تست فقط خود کامپوننت رندر میشه و کامپوننت‌های داخلی اون کامپوننت رندر نمیشن تا توجه و تمرکز روی خود کامپوننت والد باشه

#### Polyfill 
در جاوااسکریپت به یک کد یا تکنیک اشاره دارد که برای پشتیبانی از ویژگی‌های جدید جاوااسکریپت در مرورگرهایی که این ویژگی‌ها را پشتیبانی نمی‌کنند، استفاده می‌شود.
مثل استفاده از `EcmaScript` در مروگرهای قدیمی

#### Utility Types in TypeScript 
- `Partial<Type>`
  - همه اعضای تعریف شده را اختیاری میکند
- `Required<Type>`
  - همه اعضای تعریف شده را اجباری می کند
- `Readonly<Type>`
   -  از یک تایپ موجود یک تایپ جدید بسازیم که همهٔ پراپرتی‌های اون Readonly هستن.
- `Record<Keys, Type>`
   - اگه می‌خوایم تایپی داشته باشیم که با اون بتونیم نوع دقیق اسم و مقدار پراپرتی‌های آبجکت‌هامون رو مشخص کنیم، تایپ Record به کمکمون میاد:
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
   - اگه یک تایپ داریم و می‌خوایم از اون، یک تایپ جدید که شامل فقط پراپرتی‌های دلخواه ما باشه داشته باشیم، می‌تونیم از Pick استفاده کنیم:
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
  - برعکس pick اون هایی که نمیخواهیم را وارد می کنیم


#### RESTful API
- HEAD Method  
  وقتی توی یک درخواست HTTP از متد HEAD استفاده می‌کنیم، به معنی هست که از Response فقط به اطلاعات Header احتیاج داریم. بنابراین توی Response این درخواست، body وجود نخواهد داشت.


- OPTION Method  
اگه می‌خوایم اطلاعاتی کلی درباره قوانین و نحوهٔ تعامل با API مد نظر (مثل متدهای HTTP قابل استفاده و یا مجوز CORS) داشته باشیم، از این متد استفاده می‌کنیم. شاید دقت کرده باشین که مرورگر هنگام بررسی CORS، ابتدا یک درخواست با متد OPTION به آدرس مد نظر میزنه تا CORS رو بررسی کنه.

#### picture Tag
زمانی که میخواهیم در حالت رسپانسیو از سایز های مختلف عکس استفاده کنیم از این تگ استفاده میکنیم
```
<picture>
  <source media="(min-width: 900px)" srcset="img-large.jpg">
  <source media="(min-width: 600px)" srcset="img-medium.jpg">
  <img src="img-small.jpg">
</picture>
```

#### what is d.ts in TypeScript
اگه تعداد Type Declaration ها زیاد بشه بهتره اونها رو منتقل کنیم به یک فایل مجزا. چنین کاری توی تایپ‌اسکریپت با ساختن فایل .d.ts انجام می‌گیره. توی این فایل فقط می‌تونیم Type Declaration بنویسیم و کدهای دیگه‌ای از تایپ‌اسکریپت معتبر نیستن.


#### Map vs WeakMap
هر دو توی جاوااسکریپت Data Structure اختصاصی هستن که برای نگهداری مجموعه‌ای از اطلاعات به صورت Key/value استفاده میشن. مجموعهٔ WeakMap بیشتر به منظور مصرف بهینهٔ حافظه معرفی شده و تفاوت های زیر را با MAP دارد
1. کلیدهاش حتما باید آبجکت یا symbol باشد
2. قابل پیشمایش نیستن
3. پراپرتی هایی مثل `size` , `clear`, `forEach` , `entries` ندارند.


#### Closure  (کلوژرها)
یک مفهوم در جاوا اسکریپت است که از تکنیک Currying برنامه نویسی استفاده می کند یعنی استفاده از پارامترهای فانکشن پدر در فرزند بعد از فراخوانی

```
function outerFunction(x) {
  return function innerFunction(y) {
    console.log(x + y);
  }
}

let closure = outerFunction(10);

closure(5); // 15

```

#### preload vs prefetch
هر دو برای دانلود ریسورس ها هست اولی اولویت را به بالاترین حد میبره دومی اولیتش پایین میاد
```
<link rel="preload" href="/font.woff" as="font" />
<link rel="prefetch" href="/prism.js" as="script" />
```

#### Type vs Interface
برای داشتن یک تایپ برای یک مقدار Primitive (مثل رشته و عدد) فقط می‌تونیم از Type استفاده کنیم. به عبارت دیگه، از Interface فقط می‌تونیم برای مقادیر آبجکتی استفاده کنیم

در `Implement` شدن هم تفاوت دارند تایپ ها با `|` پیاده سازی می شوند ولی اینترفیس ها یا کلمه کلیدی `Implement`

#### Core Web Vitals 
به ۳ معیار مهم گفته میشه که توسط گوگل برای بررسی عملکرد یک وبسایت معرفی شده.
1. Largest Contentful Paint (LCP)  
   زمانی که بزرگترین محتوای قابل نمایش یک صفحه وب بارگذاری می‌شود
2. First Input Delay (FID)  
   زمان تأخیر اولین ورودی کاربر (مثلاً کلیک یا تپ) تا زمانی که مرورگر به درخواست واکنش می‌دهد
3. Cumulative Layout Shift (CLS)  
   مجموع تغییرات چیدمان صفحه به میزان کلیک‌ها یا تغییرات محتوا، که بر تجربه کاربری ناشی از جابه‌جایی ناگهانی و آزاد اجزای صفحه تأثیر می‌گذارد

#### CORS ( Cross-Origin Resource Sharing )
    به یعنی به اشتراک‌گذاری منابع برای درخواست‌هایی از منابعی غیر از سرور خودی هست.


### em vs rem
- em  
  از فوت سایز والد خودش میخونه
- rem  
  از فونت سایز root میخونه

### Call Stack  
یک ابزار هست که جاوااسکریپت با اون اجرای توابع توی برنامه رو مدیریت می‌کنه و مشخص می‌کنه برنامه توی چه مرحله‌ای هست و چه توابعی در صف اجرا هستن.

### prototype
هر مقداری که توی جاوااسکریپت تعریف می‌کنیم، یک سری از ویژگی‌هاش رو از یک نمونهٔ اولیه به ارث می‌بره
مثل `length` در آرایه

### Pseudo-elements vs Pseudo-classes
```
// Pseudo-elements در دام دیده می شوند
a::after { }, a::before { }


// Pseudo-classes در دام دیده نمی شوند
a:hover { }, a:focus { } , ...
```

### for...in
پیشمایش بروی یک آبجکت و بسیار هزینه بر است بخاطر وجود پروتوتایپ های آبجکت

### Web Components
- Advantages  
  Reusable, Encapsulated
- terms
   1. Custom Elements
   2. Shadow DOM
   3. HTML Templates
   4. HTML Imports 


### gzip
یک الگوریتم و قابلیت هست که باید توی سرور فعالسازی و کانفیگ بشه و هدف اون فشرده‌سازی و کاهش دادن اندازهٔ فایل‌هایی هست که از سرور به سمت کلاینت فرستاده میشن. یکی از تکنیک های افزایش سرعت در برنامه های وب است

### void and never in typescript
void یعنی تابع خروجی ندارد never یعنی تابع هیچ وقت به خروجی نمیرسد

### JavaScript types  
['null','undefined', 'string', 'number', 'boolean', 'object', 'symbol', 'bigint']

### Event Propagation
به معنا گسترش یا تکثیر یعنی با هر کلیک روی یک المنت همه پدر هایش هم کلیک می شود.

### Event Bubbling  
وقتی روی یک `DOM` فرزند کلیک میکنیم همه  پدرها تا ریشه کلیک می شوند.

### Event Capturing
دومین پارامتر `addEventListener` است که اگر `true` بشه مسیر صدا زدن ایونت ها برعکس میشه یعنی اول پدر اجرا میشه میاد به پایین

### event.preventDefault()
این متد وقتی روی یک المنت اعمال میشه، مانع عملکرد ذاتی اون المنت میشه. مثلا وقتی رو یک `form` اعمال بشه، مانع ثبت شدن فرم میشه. وقتی روی یک تگ `a` اعمال بشه، باعث میشه اون لینک کار نکنه.

### event.stopPropagation()
عملیات `Propagation` را متوقف می کند.

### event.target vs event.currentTarget  
به طور خلاصه، event.target به عنصری اشاره می‌کند که رویداد را فعال کرده است، در حالیکه event.currentTarget به عنصری اشاره دارد که هندلر رویداد به آن اتصال دارد. 

### Double NOT !!
وقتی پشت یک عملگر قرار میگیرد اون را بولین میکند

### Hoisting 
معنای تحت‌الفظی کلمه Hoisting "بالا بردن" هست. توی جاوااسکریپت قبل از اینکه کدهای ما به شکل واقعی اجرا بشن، همه‌ی توابع و متغیرها به اول حوزه‌ی خودشون جابجا میشن. به همین دلیل هست که کد زیر بدون خطا کار می‌کنه:
```
smile();

function smile() {
    return ":)";
}
```

### IIFE (  Immediately Invoked Function Expression )
 به تابعی گفته میشه که به محض اینکه تعریف شد، فراخوانی بشه.
 ```
 (function () { })();
 ```

### apply , call, bind
 با متد  `call` , `apply` می‌تونیم یه کاری کنیم که this توی یک تابع به آبجکت دلخواه ما اشاره کنه.   
 تفاوت اونها توی نحوه‌ی استفاده از اونهاست. توی متد apply ما آرگومان‌ها رو با یک آرایه پاس می‌دادیم. اما توی call باید بصورت جدا جدا پاس بدیم. مثال سوال قبل رو در نظر بگیرید:   
 ```
 add.call(item1, 3, 2, 1);
 add.apply(item1, [3, 2, 1]);
 ```

### sum in reduce 
 ```
 [1, 2, 3, 4].reduce((total, currect) => total + currect);
 ```

### localStorage vs sessionStorage vs Cookies vs IndexedDB

### arrow function vs traditional function

### Rest vs Spread

### Implicit Coercion vs Explicit Coercion
این‌ها دو روش تبدیل نوع داده توی جاوااسکریپت هستن.
- ‌‌Implicit Coercion یا ضمنی   
``` console.log(1 + '6');  ```
- Explicit Coercion یا صریح   
```  console.log(1 + parseInt('6')); ```

### freeze vs seal 
این متدها برای آبجکت سراسری Object هستن. seal به معنی بستن و خاتمه‌دادن هست. متد seal مانع اضافه شدن پراپرتی جدید به آبجکت میشه. همچنین یک پراپرتی نمی‌تونه حذف بشه. فقط میشه مقدار یک پراپرتی رو ویرایش کرد. متد freeze شبیه به seal هست اما با این تفاوت که این متد اجازه ویرایش مقدار یک پراپرتی رو نمیده.