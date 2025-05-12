
1. #### static class
- کلاسی که قابل ارث بری نیست.
- معمولا برای گسترش کلاس های پیش فرض استفاده می شود مثلا کلاس استرینگ C# را گسترش دهیم.(Extension Methods)
- نیاز به وهله سازی ندارد.
1. #### partial class
-  تعریف یک کلاس که اجزای آن در بیش از یک فایل قرار دارند است. به عبارت دیگر، یک کلاس ممکن است در چندین فایل مختلف تعریف شود و هر بخش از آن در یک فایل جداگانه قرار داشته باشد. این قابلیت برای کلاس‌های بزرگ و پیچیده مفید است که تعداد اعضا و روش‌های فعالیتشان زیاد است.
 
```
// MyClass1.cs
public partial class MyClass {
   // تعریف بخش اول کلاس
}

// MyClass2.cs
public partial class MyClass {
   // تعریف بخش دوم کلاس
}

// MyClass3.cs
public partial class MyClass {
   // تعریف بخش سوم کلاس
}
```

1. #### abstract class
قابلیت نمونه سازی از این کلاس وجود ندارد و فقط برای ارث بری است
1. #### sealed class

آخرین کلاس در زمان ارث بری است و دیگر از این کلاس نمیشه ارث بری کرد.

1. #### Reflection
به معنا انعکاس برای استخراج متا از آبجکت و کلاس استفاده می شود.

1. #### Object
به شی نمونه سازی شده از کلاس میگویند.

1. #### Abstraction
به معنای انتزاع و چیز هایی را که کاربر نیاز داره فقط ببینه راننده میدونه گاز بده ماشین حرکت میکنه ولی نیاز نیست بدونه موتور چجوری کار میکنه.

1. #### Overriding
متدی که در کلاس پدر استفاده شده و در فرزند میخواد بازنویسی بشود از این مفهوم استفاده می شود
1. #### Overloading
همون مفهوم پلی مورفیسم یعنی تعریف چند متد با تعداد پارامترهای مختلف
1. #### bstract vs interface
- اینترفیس از خاصیت multiple inhirtance پشتیبانی میکنه ولی abstract نه.
- abstract میتوان یک کلاس را تعرف و پیاده سازی کرد ولی اینترفیس فقط میشه تعریف کرد.
- abstract را برای مواقعی که حتما لازم نیست متدها پیاده سازی شوداستفاده میشود
- interface به هیچ عنوان کانستراکتور ندارد 
- هیچکدام قابلیت نمونه سازی ندارند.

1. #### out, ref, params
- در params از پشت ورودی یک تابع بیاید این ورودی تعداد نامشخص ورودی میگیرد
- در out لازم نیست مقدار اولیه بگیرد ولی ref حتما باید مقدار اولیه بگیرد

1. #### Extension Methods
زمانی که یک متد برای کلاسی که به آن دسترسی ندارم بخواهیم تعریف کنیم مثلا متدی برای کلاس string  در خود هسته #C بخواهیم تعریف کنیم.

1. #### Encapsulation 
![image](https://github.com/ehsanlotfi/cheatsheets/assets/25532726/7b17b920-4f98-4c00-9630-ce8a8536ff69)

اگر یک کلاسی سطح دسترسی آن مشخص نشود پیش فرض internal قرار میگرد.
1. #### public
دسترسی کامل در کلاس فعلی و همه کلاس ها و همه پروژه که اسمبلی شده از این کلاس
1. #### private
فقط در کلاس جاری قابل دسترسی است و لا غیر
1. #### internal
در همه کلاس های پروژه فعلی استفاده می شود و نه در پروژه های اسمبلی
1. #### protected
1. #### protectedInternal

1. #### onstractor of class


#1. #### کانستراکتور پیش فرض: 
این کانستراکتور برای ساخت شی‌های پیش فرض مورد استفاده قرار می‌گیرد و به صورت خودکار فراخوانی می‌شود.

#1. #### کانستراکتور پارامتری:
در این نوع کانستراکتور، پارامترهایی به آن ارسال می‌شوند که برای مقداردهی اولیه خصوصیات شی‌ها استفاده می‌شوند.

#1. #### کانستراکتور استاتیک: 
این نوع کانستراکتور برای ایجاد متد‌های استاتیک به کار می‌رود و هنگام بارگذاری یک کلاس، فقط یک بار فراخوانی می‌شود.

## throw vs throw x
throw اطلاعات بیشتری بر میگرداند

## ArrayList vs HashTable 
1. #### ArrayList
در افزودن کلید نیاز ندارد
1. #### HashTable
در افزودن کلید نیاز دارد.


## IEnumerable Vs IQueryable
1. #### IEnumerable
برای کار با مجموعه داده‌های در حافظه مانند لیست‌ها، آرایه‌ها و ... استفاده می‌شود.
1. #### IQueryable
برای لیست هایی که از سمت دیتابیس می آید و برای Linq کاربرد دارد.  و ممکن است در لحظه تغییر کند.  با استفاده از Expression Tree اجازه می‌دهد تا پرس و جوهای LINQ به صورت تاخیری (Deferred Execution) اجرا شوند،

بنابراین، اگر تنها نیاز به پیمایش داده‌ها در حافظه دارید، از IEnumerable استفاده کنید؛ اما اگر نیاز به اعمال پرس و جوی پیچیده‌تری در داده‌ها دارید که باید به صورت تاخیری اجرا شود، از IQueryable استفاده کنید.

## Delegate VS Event 
یک  پوینتر است که میتوان رفرنس یک یا چند متد را توی خودش نگه داره پارامتری که بهDelegate پاس داده میشه خودش یک متد است. از جمله پیاده سازی الگوهای طراحی Observer و Callback استفاده می‌شود.
```
// Delegate simple Example
internal class Program
{
    public delegate int MyDelegate(params int[] numbers);
    public static int Add(params int[] numbers) => numbers[0] + numbers[1];
    public static int Square(params int[] numbers) => numbers[0] * numbers[0];

    public static void Main(string[] args)
    {
        MyDelegate myDelegate = Add;
        var add_res = myDelegate(5, 3); // Output: 8

        myDelegate = Square; 
        var square_res = myDelegate(5); // Output: 25
    }
}
```
1. #### Anonymous Delegate
دلیگیتی که متد را داخلی خودش میسازه و نیاز به فراخوانی متد ثالث ندارد.
1. #### Multicast Delegate
میتواند چندین متد را داخل آن رفرنس دهی کرد.
1. #### Event
به صورت مجموعه ای از delegate ها عمل می کند که به تابعی object را متصل کرده و یک مشتری برای کاربر سازی می دهد. هنگامی که یک event در سیستم رخ داد، delegate های متصل به آن فراخوانی می شوند و بدین ترتیب کار کاربر ادامه پیدا می کند.
به طور خلاصه، delegate به عنوان یک پوینتر به تابع عمل می کند، در حالی که event به عنوان یک پوینتر به بازخورد استفاده می شود.



## this
اشاره به نمونه ای که داخل کلاس داریم

## const vs readonly
const در زمان تعریف باید مقدار دهی شود 
readonly میتوان در کانستکراتور مقدار دهی شود

## var vs dynamic 
var متغیر کامپایل تایم تعریف میکند 
dynamic متغیر ران تایم تعریف میکند

## Boxing vs unboxing
وقتی یک مقدار value type را داخل refrence type میریزیم باکسینگ رخ میدهد و زمانی که تایپ کستینگ میکنم  unboxing رخ میدهد
## sring vs string builder
برای الحاق رشته ها فضای جدید میگیرد ولی در string builder فضای جدید نمیگیرد.

![1690059293383](https://github.com/ehsanlotfi/cheatsheets/assets/25532726/d45754fd-9071-4190-851c-fa53e8b39691)

## Is vs As
- As برای مشخص کردن تایپ یک مقدار 
- Is برای چک کردن تایپ یک مقدار

## Semaphore
Semaphore برای کنترل دسترسی به منابع محدود در برنامه‌های همزمان استفاده می‌شود. در دات‌نت، از کلاس‌های Semaphore و SemaphoreSlim استفاده می‌کنیم، و در زبان‌های دیگر مانند Python از threading.Semaphore استفاده می‌شود. 

```
using System;
using System.Threading;

class Program
{
    static Semaphore semaphore = new Semaphore(2, 2); // حداکثر دو thread اجازه دسترسی دارند.

    static void Main()
    {
        for (int i = 0; i < 5; i++)
        {
            new Thread(Worker).Start(i);
        }
    }

    static void Worker(object id)
    {
        Console.WriteLine($"Thread {id} منتظر است");
        semaphore.WaitOne(); // منتظر دسترسی به منبع می‌ماند.
        Console.WriteLine($"Thread {id} وارد شد");

        Thread.Sleep(2000); // شبیه‌سازی کار با منبع

        Console.WriteLine($"Thread {id} خارج شد");
        semaphore.Release(); // دسترسی به منبع آزاد می‌شود.
    }
}

```
در این مثال، حداکثر دو thread می‌توانند به‌طور همزمان به بخش محافظت شده دسترسی داشته باشند. بقیه thread ها باید منتظر بمانند تا یکی از thread های فعال منبع را آزاد کند.


1. #### 1 - Nullable Reference Types
```
  string name = null; // ERROR
  string? name = null; // OK!
```
1. #### 2 - Default implementations in interfaces
 اگر یک کلاس از یک اینترفیس که حاوی متد پیش‌فرض است، این متد را پیاده‌سازی نکرده باشد، متد پیش‌فرض اجرا می‌شود و کد تعیین شده در آن اجرا می‌شود. در کد زیر متد Show() به پیاده سازی پیش فرض قابل استفاده است.
```
using System

public interface IExample
{
    void Display();
    void Show()
    {
        Console.WriteLine("Default implementation of Show method");
    }
}

public class MyClass : IExample
{
    public void Display()
    {
        Console.WriteLine("Display method implementation");
    }
}

class Program
{
    static void Main()
    {
        MyClass obj = new MyClass();
        obj.Display();  // اجرای متد Display
        obj.Show();     // اجرای متد پیش‌فرض Show
    }
}

```
1. #### 3 - Ranges
استفاده از سه نقطه برای تعریف آرایه
```
int[] numbers = { 0, 1, 2, 3, 4, 5 };
var range = 1..4; // بازه از اولین عنصر تا سومین عنصر
var result = numbers[range]; // result = {1, 2, 3}
```
1. #### 4 - Indices

از نماد ^ برای نمایش اندیس از انتها استفاده می‌شود. مثلاً ^2 به عنوان اندیس دومین عنصر از انتها شناخته می‌شود.
```
int[] numbers = { 0, 1, 2, 3, 4, 5 };
var index = ^2; // اندیس دومین عنصر از انتها
var result = numbers[index]; // result = 4
```
1. #### 4 - improve interpolated verbatim strings
استفاده از $@ برای استفاده از کدهای C# درون رشته
```
  string message = $@"Hello, my name is {name} and I am {age} years old.";
```
1. #### 5 - improve local functions
توابع محلی، امکان تعریف یک تابع را درون یک متد، فراهم می‌کنند.
1. #### 6 - improve Null Coalescing Assignment
اگر متغیر مورد نظر نال باشد مقدار پیش فرض اعمال می شود.
```
  string name = null;
  name ??= "Default Name";
  Console.WriteLine($"Name: {name}");
```
1. #### 7 - improve Pattern Matching
 این ویژگی بهبودهایی را به نحوه کار با switch statements و is expressions اضافه می‌کند.
```
var operation = "+";
int a = 1, b = 2;
var result = operation switch
{
   "+" => a + b,
   "-" => a - b,
   "/" => a / b,
     _ => throw new NotSupportedException()
};
```
```
object obj = "Hello";

if (obj is int i)
{
    Console.WriteLine($"It's an int with value {i}");
}
else if (obj is string s)
{
    Console.WriteLine($"It's a string with value {s}");
}
else
{
    Console.WriteLine("It's something else");
}
// It's a string with value Hello
```
1. #### 8 - using declarations
تا پیش از C# 8.0، روش متداول کار با عبارات using به صورت زیر است و به آن استفاده از using statements گفته می‌شود:
```
 using (var reader = new StreamReader(file))
  {
      var s = reader.ReadToEnd();
  }
```
که در نهایت پس از پایان این قطعه کد، شیء reader به صورت خودکار Dispose می‌شوند. اکنون در C# 8.0 می‌توان قطعه کد فوق را به کمک using declarations به صورت زیر خلاصه کرد. که در اینجا پرانتزها و همچنین {} ها، حذف شده‌اند.
```
 using StreamReader reader = new StreamReader(file);
 var s = reader.ReadToEnd();
```


1. #### 9 - Async Streams
 در جریان از داده‌ها را به صورت همروند و ناهمزمان میتوان استفاده کرد.
```
await foreach (var number in GenerateNumbersAsync())
  {
      Console.WriteLine(number);
  }
```



1. #### 1 -  Target Typing 
1. #### 2 - Top level statements
با Top-level statements، شما می‌توانید کد خود را به صورت ساده‌تر بنویسید بدون نیاز به اعلام کلاس یا تابع Main. به عبارت دیگر، شما می‌توانید دستورات اجرایی برنامه خود را در بالای فایل بنویسید بدون این که به یک کلاس یا تابع خاصی محدود شوید.
```
using System;
Console.WriteLine("Hello, World!");
```
1. #### 3 - Init-Only, record feature
با ویژگی Init-Only، شما می‌توانید تعیین کنید که کدام خاصیت تنها در زمان ایجاد نمونه (instantiation) قابل تنظیم باشد و پس از آن قفل گردد. در مثال زیر شی Person یک بار مقادیرش پر می شود و دیگر نمیتوان تغییر کند.
```
public record Person
{
    public string FirstName { get; init; }
    public string LastName { get; init; }
}

```
1. #### 4 - AND، OR, NOT
1. #### 5 - Covariant returns (کوواریانت)
این ویژگی در C# 9 است که به برنامه‌نویسان این امکان را می‌دهد که نوع بازگشتی یک متد را در کلاس‌های مشتق (Subclasses) تغییر دهند، بدون این که نیاز به کست کردن داشته باشند.
1. #### 6 -  Module initializer
این ویژگی امکان اجرای کد در زمان بارگذاری ماژول (module) را فراهم می‌کند. ماژول در اینجا به یک فایل DLL یا EXE اشاره دارد. استفاده از آن مفید است زمانی که نیاز دارید کدی را قبل از شروع اجرای توابع اصلی برنامه اجرا کنید. به عبارت دیگر، می‌توانید مراحلی مانند پیکربندی یا آماده‌سازی محیط را در زمان بارگذاری ماژول انجام دهید.
```
using System;
using System.Runtime.CompilerServices;

public class MyModuleInitializer
{
    [ModuleInitializer] // این attribue باعث میشه کلاس ما به عنوان ModuleInitializer شناخته شود
    public static void Initialize()
    {
        Console.WriteLine("Module Initialization Code");
    }
}

public class Program
{
    static void Main()
    {
        Console.WriteLine("Main Method");
    }
}

```

1. #### 7 -  Lambdas 
1. #### 8 - Attributes on local functions

1. #### 0 - Global using directives
یا این ویژگی ما نیازی به تعریف  directives در ابتدای هر فایل نداریم و میتوان همه directives مشترک را در یک فایل ذخیره کرد.
```
<ImplicitUsings>enable</ImplicitUsings>
```
1. #### 1 - Record structs
1. #### 2 - Improvements of structure types
1. #### 3 - Interpolated string handler
1. #### 4 - Global using directives
1. #### 5 - File-scoped namespace declaration
1. #### 6 - Extended property patterns
1. #### 7 - Lambda expression improvements
1. #### 8 - Constant interpolated strings
1. #### 9 - Record types can seal ToString
1. #### 10 - Assignment and declaration in same deconstruction
1. #### 11 -  definite assignment
1. #### 12 - Allow AsyncMethodBuilder attribute on methods
1. #### 13 - CallerArgumentExpression attribute diagnostics
1. #### 14 - Enhanced #line pragma


1. #### 1 - Generic attributes
1. #### 2 - Generic math support
1. #### 3 - Numeric IntPtr and UIntPtr
1. #### 4 - Newlines in string interpolations
1. #### 5 - List patterns
1. #### 6 -  method group conversion to delegate
1. #### 7 - Raw string literals
1. #### 8 - Auto-default struct
1. #### 9 - Pattern match Span<char> or ReadOnlySpan<char> on a constant string
1. #### 10 - Extended nameof scope
1. #### 11 - UTF-8 string literals
1. #### 12 - Required members
1. #### 13 - ref fields and ref scoped variables
1. #### 14 - File local types

1. #### 1 - Primary constructors
1. #### 2 - Collection expressions
1. #### 3 - ref readonly parameters
1. #### 4 - Default lambda parameters
1. #### 5 - Alias any type
1. #### 6 - Inline arrays
1. #### 7 - Experimental attribute
1. #### 8 - Interceptors
