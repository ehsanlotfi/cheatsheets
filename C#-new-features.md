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
### 3 - Ranges & Indices
### 4 - 
### 4 - 
### 5 - 
### 6 - 
### 7 - 
### 8 - 
### 9 - 
