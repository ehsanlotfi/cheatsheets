1. #### ng-template vs ng-container
    - ng-template:
        - It is used to define a template that is not rendered directly in the `DOM`.
        - It will only be displayed when a condition is met (e.g., using `*ngIf` or `*ngFor`).
        - It does not appear in the `DOM` unless activated.
    - ng-container:
        - It is a virtual element that does not create an extra tag in the `DOM`.
        - Used to group multiple elements without affecting the structure of the `DOM`.
            - Suitable for applying directives like `*ngIf` and `*ngFor`
 
1. #### pure pipe vs impure pipe
    - Pure Pipe: Called only when the input value changes (default behavior).
    - Impure Pipe: Called on every change detection cycle, regardless of input changes.

### Annotation vs Decorator
 فرقی پیدا نکردم فقط Annotation ها درون کلاس استفاده می شود برای تعریف یک متغیر مثل `()Input@` ولی Decorator برای تعریف یک کلاس استفاده می شود مثل `()component@` 
### Observable vs Promise 
 هر دو برای کارهای غیرهمزمان در جاوااسکریپت کاربرد دارد اما promise ها یک ایونت را هندل می کنند و قابل کنسل شدن نیستند ولی observable استریم هستند و همزمان میتونن چند جواب برگردونن و قابل کنسل شدن هستند.
### Lazy loading vs Eager loading
لیزی لود یعنی همه اسکریپت های پروژه در لود اولیه نیایند ولی هر ماژول لود خودش را داشته باشه
### ViewChild VS ContentChild
هر دو برای دسترسی به المان های DOM استفاده می شود ولی ViewChild برای دسترسی به المان های داخل کامپوننت کاربرد دارد ولی ContentChild برای دسترسی به المان های داخل `<ng-content>` کاربرد دارد.

### Unit Test ( Jasmine , Karma  )
در آنگولار، تست واحد با استفاده از فریمورک Jasmine برای نوشتن ادعای تست (test assertions) و ابزار Karma برای اجرای تست‌ها انجام می‌شود.

### HMR (Hot Module Replacement ) vs Hot reload
قسمتی از صفحه بروز می شود و استیت ها تغییر نمیکند 

## Subjects
- #### Subject in Rxjs
مشترکین بعد از عضو شدن به سابجکت میتوانند خروجی ها را دریافت کنند. آخرین مقدار که قبلا منتشر شده را ندارند
- #### BehaviorSubject
مشترکین جدید آخرین مقدار منتشر شده یا مقدار اولیه را بلافاصله پس از اشتراک دریافت می کنند.
- #### ReplaySubject
مشترکین جدید تمام مقادیر منتشر شده قبلی را بلافاصله پس از اشتراک دریافت می کنند
- #### AsyncSubject
پس از تکمیل آخرین مقدار نکس شده را همه دریافت میکنند. 

- #### MergeMap, FlatMap  in Rxjs
مرج مپ نسخه جدید فلت مپ هست درخواست ها باهم ارسال میشوند و بدون در نظر گرفتن ترتیب هر کدوم تمام شد بر میگردد. 

- #### ConcatMap in Rxjs
درخواست بصورت سری و با توجه به زمان تمام شدن قبلی بر میگردد

- #### SwitchMap in Rxjs
درخواست ها ارسال میشود به محض دریافت درخواست جدید درخواست قبلی کنسل می شود و به درخواست آخری پاسخ داده می شود مثلا برای استفاده در کادر جستجو

- #### ExhaustMap in Rxjs
برعکس سوئیچ مپ فقط درخواست اول پاسخ داده میشود بقیه همه کنسل می شود
