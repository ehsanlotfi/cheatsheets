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