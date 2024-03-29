# FROM
```
FROM <image>
FROM <image>:<tag>
FROM <image>@<digest>
```
- باید اولین دستور داکر فایل تعریف شود و به معنا این است از چه ایمیجی استفاده کند
- میتواند چندین بار برای استفاده از چندین ایمیج در یک داکر فایل استفاده شود
-  tag و digest بصورت اختیاری قابل تعریف است اگر تعریف نشود آخرین نسخه در نظر گرفته می شود 
- اگر تگ پیدا نشود خطا صادر میکند

# MAINTAINER
```
MAINTAINER <name>
```
- نام نویسنده ایمیج را مشخص می کند.

# RUN
```
RUN <command> (shell form, the command is run in a shell, which by default is /bin/sh -c on Linux or cmd /S /C on Windows)
RUN ["<executable>", "<param1>", "<param2>"]

// example
RUN apt-get update

```
- برای اجرای دستور روی ایمیج پیش فرض استفاده می شود.
- برای تغییر ایمیج پیش فرض از ```SHELL``` استفاده می شود. 

# CMD
```
CMD ["<executable>","<param1>","<param2>"] (exec form, this is the preferred form)
CMD ["<param1>","<param2>"] (as default parameters to ENTRYPOINT)
CMD <command> <param1> <param2> (shell form)
```

- برای اینکه یه دستوری رو به ایمیج ساخته شده معرفی بکنی که همیشه اونو اجرا بکنه.
- فقط یک دستور ```CMD``` در داکر فایل میتواند وجود داشته باشد.
- اگر چند تا ```CMD``` داشته باشید فقط آخرین آن مورد اجرا است.

# LABEL
```
LABEL <key>=<value> [<key>=<value> ...]
```

- با این دستور میتوان یکسری متادیتا به ایمیج اضافه کرد.

# EXPOSE
```
EXPOSE <port> [<port> ...]
```
- جنبه نمایشی دارد و به داکر می گوید ایمیج من فلان پورت ها را خروجی می دهد.
- این دستور پورت های کانتینر را در دسترس میزبان قرار نمی دهد.

# ENV
```
ENV <key> <value>
ENV <key>=<value> [<key>=<value> ...]
```
- متغیرهای محلی ایمیج را مشخص می کند.


# ADD
```
ADD <src> [<src> ...] <dest>
ADD ["<src>", ... "<dest>"] (this form is required for paths containing whitespace)
```
- فایل‌ها، دایرکتوری‌ها یا آدرس‌های اینترنتی فایل خارجی را از <src> کپی می‌کند و آنها را به سیستم فایل تصویر در مسیر <dest> اضافه می‌کند.


# COPY
```
COPY <src> [<src> ...] <dest>
COPY ["<src>", ... "<dest>"] (this form is required for paths containing whitespace)
```
 - مشابه دستور ```ADD``` عمل می کند.
  
# ENTRYPOINT
Usage:
```
ENTRYPOINT ["<executable>", "<param1>", "<param2>"] (exec form, preferred)
ENTRYPOINT <command> <param1> <param2> (shell form)
```

- به شما این امکان را می دهد تا یک کانتینر را پیکربندی کنید که به عنوان یک فایل اجرایی اجرا شود.
 - اجرا کردن یک دستور بعد از ساخته شدن Container


  
# VOLUME
```
VOLUME ["<path>", ...]
VOLUME <path> [<path> ...]
```
 - اضافه کردن یک mount point در ماشین میزبان یا Containerهای دیگر.
 
# USER
```
USER <username | UID>
```
- ست کردن یک user یا UID در Container

# WORKDIR
```
WORKDIR </path/to/workdir>
```
- ست کردن دایرکتوری اجرایی در Container

# ARG
```
ARG <name>[=<default value>]
```
- متغیری را تعریف می‌کند که کاربران می‌توانند در زمان ساخت به سازنده با آن ارسال کنند مانند ```docker build``` دستوراتی که داخل فلگ ```--build-arg <varname>=<value>``` می آید.
 
# ONBUILD
```
ONBUILD <Dockerfile INSTRUCTION>
```
- دستورات را بصورت ```trigger``` اضافه میکند تا در زمان دیگری استفاده شود.
# STOPSIGNAL
```
STOPSIGNAL <signal>
```
- دستورالعمل سیگنال فراخوانی سیستم را تنظیم می کند که برای خروج به کانتینر ارسال می شود.

# HEALTHCHECK
```
HEALTHCHECK [<options>] CMD <command> (check container health by running a command inside the container)
HEALTHCHECK NONE (disable any healthcheck inherited from the base image)
```
- به داکر می‌گوید چگونه یک ایمیج را تست کند تا بررسی کند که هنوز کار می‌کند.

# SHELL
```
SHELL ["<executable>", "<param1>", "<param2>"]
```
- شل پیش فرض را برای اجرا دستورات مشخص می کند.
