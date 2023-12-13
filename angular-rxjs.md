
# Rxjs cheat sheet 
## Subjects
- #### Subject
مشترکین بعد از عضو شدن به سابجکت میتوانند خروجی ها را دریافت کنند. آخرین مقدار که قبلا منتشر شده را ندارند
- #### BehaviorSubject
مشترکین جدید آخرین مقدار منتشر شده یا مقدار اولیه را بلافاصله پس از اشتراک دریافت می کنند.
- #### ReplaySubject
مشترکین جدید تمام مقادیر منتشر شده قبلی را بلافاصله پس از اشتراک دریافت می کنند
- #### AsyncSubject
پس از تکمیل آخرین مقدار نکس شده را همه دریافت میکنند. 


## Operators

- #### MergeMap, FlatMap
مرج مپ نسخه جدید فلت مپ هست درخواست ها باهم ارسال میشوند و بدون در نظر گرفتن ترتیب هر کدوم تمام شد بر میگردد. 

- #### ConcatMap
درخواست بصورت سری و با توجه به زمان تمام شدن قبلی بر میگردد

- #### SwitchMap
درخواست ها ارسال میشود به محض دریافت درخواست جدید درخواست قبلی کنسل می شود و به درخواست آخری پاسخ داده می شود مثلا برای استفاده در کادر جستجو

- #### ExhaustMap

برعکس سوئیچ مپ فقط درخواست اول پاسخ داده میشود بقیه همه کنسل می شود