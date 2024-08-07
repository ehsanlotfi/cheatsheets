
## type of class
### static class
- کلاسی که قابل ارث بری نیست.
- معمولا برای گسترش کلاس های پیش فرض استفاده می شود مثلا کلاس استرینگ C# را گسترش دهیم.(Extension Methods)
- نیاز به وهله سازی ندارد.
### partial class
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

### abstract class
قابلیت نمونه سازی از این کلاس وجود ندارد و فقط برای ارث بری است
### sealed class

آخرین کلاس در زمان ارث بری است و دیگر از این کلاس نمیشه ارث بری کرد.

## Reflection
به معنا انعکاس برای استخراج متا از آبجکت و کلاس استفاده می شود.

## Object
به شی نمونه سازی شده از کلاس میگویند.

## Abstraction
به معنای انتزاع و چیز هایی را که کاربر نیاز داره فقط ببینه راننده میدونه گاز بده ماشین حرکت میکنه ولی نیاز نیست بدونه موتور چجوری کار میکنه.
## Overriding vs Overloading
### Overriding
متدی که در کلاس پدر استفاده شده و در فرزند میخواد بازنویسی بشود از این مفهوم استفاده می شود
### Overloading
همون مفهوم پلی مورفیسم یعنی تعریف چند متد با تعداد پارامترهای مختلف
## abstract vs interface
- اینترفیس از خاصیت multiple inhirtance پشتیبانی میکنه ولی abstract نه.
- abstract میتوان یک کلاس را تعرف و پیاده سازی کرد ولی اینترفیس فقط میشه تعریف کرد.
- abstract را برای مواقعی که حتما لازم نیست متدها پیاده سازی شوداستفاده میشود
- interface به هیچ عنوان کانستراکتور ندارد 
- هیچکدام قابلیت نمونه سازی ندارند.

## out, ref, params
- در params از پشت ورودی یک تابع بیاید این ورودی تعداد نامشخص ورودی میگیرد
- در out لازم نیست مقدار اولیه بگیرد ولی ref حتما باید مقدار اولیه بگیرد

## Extension Methods
زمانی که یک متد برای کلاسی که به آن دسترسی ندارم بخواهیم تعریف کنیم مثلا متدی برای کلاس string  در خود هسته #C بخواهیم تعریف کنیم.

## Encapsulation 
![image](https://github.com/ehsanlotfi/cheatsheets/assets/25532726/7b17b920-4f98-4c00-9630-ce8a8536ff69)

اگر یک کلاسی سطح دسترسی آن مشخص نشود پیش فرض internal قرار میگرد.
### public
دسترسی کامل در کلاس فعلی و همه کلاس ها و همه پروژه که اسمبلی شده از این کلاس
### private
فقط در کلاس جاری قابل دسترسی است و لا غیر
### internal
در همه کلاس های پروژه فعلی استفاده می شود و نه در پروژه های اسمبلی
### protected
### protectedInternal

## constractor of class


#### کانستراکتور پیش فرض: 
این کانستراکتور برای ساخت شی‌های پیش فرض مورد استفاده قرار می‌گیرد و به صورت خودکار فراخوانی می‌شود.

#### کانستراکتور پارامتری:
در این نوع کانستراکتور، پارامترهایی به آن ارسال می‌شوند که برای مقداردهی اولیه خصوصیات شی‌ها استفاده می‌شوند.

#### کانستراکتور استاتیک: 
این نوع کانستراکتور برای ایجاد متد‌های استاتیک به کار می‌رود و هنگام بارگذاری یک کلاس، فقط یک بار فراخوانی می‌شود.

## throw vs throw x
throw اطلاعات بیشتری بر میگرداند

## ArrayList vs HashTable 
### ArrayList
در افزودن کلید نیاز ندارد
### HashTable
در افزودن کلید نیاز دارد.


## IEnumerable Vs IQueryable
### IEnumerable
برای کار با مجموعه داده‌های در حافظه مانند لیست‌ها، آرایه‌ها و ... استفاده می‌شود.
### IQueryable
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
### Anonymous Delegate
دلیگیتی که متد را داخلی خودش میسازه و نیاز به فراخوانی متد ثالث ندارد.
### Multicast Delegate
میتواند چندین متد را داخل آن رفرنس دهی کرد.
### Event
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