#####  Concurrency
همروندی در برنامه‌نویسی به معنای قابلیت اجرای همزمان چندین فرآیند و یا چندین نخ از یک برنامه است. اما برای استفاده بهینه از Concurrency باید از قفل گذاری و سایر مفاهیم مرتبط با همروندی نیز آگاهی داشته باشیم.

##### FMP ( First Meaningful Paint )
اولین لحظه ای کاربر میتوان محتوای صفحه را ببیند.
##### TTI ( Time to Interactive )
اولین لحظه ای که کاربر میتوان از صفحه استفاده کند.

### KISS (keep it simple and stupid)
ساده ترین روش ممکن کد بزنید و از پیچیدگی اجتناب کنید

### YANGI (You ain't gonna need it)
 شما به آن نیاز نخواهید داشت.
 چه دلیلی داره کدی بنویسید که به آن نیاز ندارید
 کدی اضاف نشود تا وقتی که نیاز آن احساس نشده
 ### DRY ( Don’t repeat yourself )
 خودت را تکرار نکن
 اگر پروژه ای را که آغاز کرده اید بسیار مهم است که هیچ وقت چیزی را دوبار تکرار نکنید.
 
 ### Shallow Copy VS Deep Copy
 مشابه رفرنس تایپ و وریبل تایپ است.

 ### LOD ( Law of Demeter )
 قانون دمیتر - هر واحد باید تنها دانش اندکی در مورد واحدهای دیگر داشته باشد و این واحدها صرفاً شامل واحدهای کاملاً مرتبط به واحد کنونی باشند. 
 # SOC ( Separation of Concerns )
 تفکیک دغدغه ها - تفکیک کردن حوزه های مختلف نرم افزار می باشد  
 
### SOLID

##### Single Responsibility
هر کلاس یا ماژول باید مسئولیت یک وظیفه مشخص را داشته باشد 

##### Open closed

یک کلاس باید در برابر تغییرات بسته باشد ولی باید قابلیت توسعه را داشته باشد
##### Liskov
اگر کلاس A از کلاس B ارث‌بری کرده باشد، در همه‌ی موارد می‌توان از شی‌ء‌های کلاس A به جای شیء‌های کلاس B استفاده کرد، بدون داشتن هیچ تفاوتی در عملکرد برنامه.

##### Dependency inversion

کلاس سطح بالاتر نباید به کلاس های سطح پایینتر وابسته باشند هر دو باید به انتزاعات وابسته باشد.
##### Interface Segregation 
اینترفیس ها اینقدر کوچک شوند که از برنامه نویس فقط به قسمتی که نیاز دارد دسترسی داشته باشد
 
 
 
### SSL (Secure Sockets Layer) OR TLS (Transport Layer Security)
 یک پروتکل امنیتی است که در اینترنت برای ارتباطات امن بین مرورگر و سرور استفاده می‌شود. SSL با استفاده از الگوریتم‌های رمزنگاری قوی، اطلاعاتی که بین مرورگر و سرور رد و بدل می‌شوند را محافظت می‌کند.



 ### JIT (Just-In-Time) VS AOT (Ahead-of-Time)
  - در جیت کد برنامه در زمان اجرا کامپایل می شود مثلا ما در مرورگر فایل های تایپ اسکریپت را داریم و و در محیط دولوپ بیشتر کاربرد دارد و تغییرات را میتونیم ببینم انعطاف پذیری بیشتری دارد.
 -  در AOT کد برنامه کامپایل شده است و بیشتر در محیط ها production کاربرد دارد و سرعت و عملکرد بیشتری دارد
 

### Parallelism vs Concurrency
پارالل یعنی این زبان می‌تونه چندین کار رو به صورت هم‌زمان و مجزا شروع و پردازش کنه. ولی همزمانی 


### Currying technique
با این تکنیک می‌تونیم بجای داشتن یک تابع با چندین پارامتر، چند تابع (تو در تو) با یک پارامتر داشته باشیم.

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
