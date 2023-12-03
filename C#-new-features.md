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
