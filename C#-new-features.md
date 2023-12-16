# C# 8.0
### 1 - Nullable Reference Types
```
  string name = null; // ERROR
  string? name = null; // OK!
```
### 2 - Default implementations in interfaces
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
### 3 - Ranges
استفاده از سه نقطه برای تعریف آرایه
```
int[] numbers = { 0, 1, 2, 3, 4, 5 };
var range = 1..4; // بازه از اولین عنصر تا سومین عنصر
var result = numbers[range]; // result = {1, 2, 3}
```
### 4 - Indices

از نماد ^ برای نمایش اندیس از انتها استفاده می‌شود. مثلاً ^2 به عنوان اندیس دومین عنصر از انتها شناخته می‌شود.
```
int[] numbers = { 0, 1, 2, 3, 4, 5 };
var index = ^2; // اندیس دومین عنصر از انتها
var result = numbers[index]; // result = 4
```
### 4 - improve interpolated verbatim strings
استفاده از $@ برای استفاده از کدهای C# درون رشته
```
  string message = $@"Hello, my name is {name} and I am {age} years old.";
```
### 5 - improve local functions
توابع محلی، امکان تعریف یک تابع را درون یک متد، فراهم می‌کنند.
### 6 - improve Null Coalescing Assignment
اگر متغیر مورد نظر نال باشد مقدار پیش فرض اعمال می شود.
```
  string name = null;
  name ??= "Default Name";
  Console.WriteLine($"Name: {name}");
```
### 7 - improve Pattern Matching
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
### 8 - using declarations
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


### 9 - Async Streams
 در جریان از داده‌ها را به صورت همروند و ناهمزمان میتوان استفاده کرد.
```
await foreach (var number in GenerateNumbersAsync())
  {
      Console.WriteLine(number);
  }
```




# C# 9.0
### 1 - Improved Target Typing 
### 2 - Top level statements
با Top-level statements، شما می‌توانید کد خود را به صورت ساده‌تر بنویسید بدون نیاز به اعلام کلاس یا تابع Main. به عبارت دیگر، شما می‌توانید دستورات اجرایی برنامه خود را در بالای فایل بنویسید بدون این که به یک کلاس یا تابع خاصی محدود شوید.
```
using System;
Console.WriteLine("Hello, World!");
```
### 3 - Init-Only, record feature
با ویژگی Init-Only، شما می‌توانید تعیین کنید که کدام خاصیت تنها در زمان ایجاد نمونه (instantiation) قابل تنظیم باشد و پس از آن قفل گردد. در مثال زیر شی Person یک بار مقادیرش پر می شود و دیگر نمیتوان تغییر کند.
```
public record Person
{
    public string FirstName { get; init; }
    public string LastName { get; init; }
}

```
### 4 - AND، OR, NOT
### 5 - Covariant returns (کوواریانت)
این ویژگی در C# 9 است که به برنامه‌نویسان این امکان را می‌دهد که نوع بازگشتی یک متد را در کلاس‌های مشتق (Subclasses) تغییر دهند، بدون این که نیاز به کست کردن داشته باشند.
### 6 -  Module initializer
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

### 7 - Improved Lambdas 
### 8 - Attributes on local functions



# C# 10.0
### 0 - Global using directives
یا این ویژگی ما نیازی به تعریف  directives در ابتدای هر فایل نداریم و میتوان همه directives مشترک را در یک فایل ذخیره کرد.
```
<ImplicitUsings>enable</ImplicitUsings>
```
### 1 - Record structs
### 2 - Improvements of structure types
### 3 - Interpolated string handler
### 4 - Global using directives
### 5 - File-scoped namespace declaration
### 6 - Extended property patterns
### 7 - Lambda expression improvements
### 8 - Constant interpolated strings
### 9 - Record types can seal ToString
### 10 - Assignment and declaration in same deconstruction
### 11 - Improved definite assignment
### 12 - Allow AsyncMethodBuilder attribute on methods
### 13 - CallerArgumentExpression attribute diagnostics
### 14 - Enhanced #line pragma



# C# 11.0
### 1 - Generic attributes
### 2 - Generic math support
### 3 - Numeric IntPtr and UIntPtr
### 4 - Newlines in string interpolations
### 5 - List patterns
### 6 - Improved method group conversion to delegate
### 7 - Raw string literals
### 8 - Auto-default struct
### 9 - Pattern match Span<char> or ReadOnlySpan<char> on a constant string
### 10 - Extended nameof scope
### 11 - UTF-8 string literals
### 12 - Required members
### 13 - ref fields and ref scoped variables
### 14 - File local types



# C# 12.0
### 1 - Primary constructors
### 2 - Collection expressions
### 3 - ref readonly parameters
### 4 - Default lambda parameters
### 5 - Alias any type
### 6 - Inline arrays
### 7 - Experimental attribute
### 8 - Interceptors
