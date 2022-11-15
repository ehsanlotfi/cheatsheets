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

# ADD
```
ADD <src> [<src> ...] <dest>
ADD ["<src>", ... "<dest>"] (this form is required for paths containing whitespace)
```

# COPY
```
COPY <src> [<src> ...] <dest>
COPY ["<src>", ... "<dest>"] (this form is required for paths containing whitespace)
```

# ENTRYPOINT

Usage:
```
ENTRYPOINT ["<executable>", "<param1>", "<param2>"] (exec form, preferred)
ENTRYPOINT <command> <param1> <param2> (shell form)
```

# VOLUME
```
VOLUME ["<path>", ...]
VOLUME <path> [<path> ...]
```

# USER
```
USER <username | UID>
```


# WORKDIR
```
WORKDIR </path/to/workdir>
```

# ARG
```
ARG <name>[=<default value>]
```

# ONBUILD
```
ONBUILD <Dockerfile INSTRUCTION>
```

# STOPSIGNAL
```
STOPSIGNAL <signal>
```

# HEALTHCHECK
```
HEALTHCHECK [<options>] CMD <command> (check container health by running a command inside the container)
HEALTHCHECK NONE (disable any healthcheck inherited from the base image)
```

# SHELL
```
SHELL ["<executable>", "<param1>", "<param2>"]
```
