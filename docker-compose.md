```
version: '3.8'

services:
    sso: // نام دلخواه سرویس
      image: identityserver:v1 // نام ایمیج اگر در لیست ایمیج های شما نباشد پیش فرض از داکرهاب استفاده میکند
      stdin_open: true // intgeractive تعاملات با کانتینر را فراهم میکند بوسیلله STDIN و STDOUT
      tty: true // روشن کردن حالت tty یعنی داکر یک ترمینال مجازی برای من ایجاد کند
      user: root
      container_name: sso // نام اختیاری کانتینر
      entrypoint: /startup.sh // بعد از اجرای کانتینر چه چیزی اجرا شود
      ports: // تنظیم کردن پورت اولی سیستم مبدا دومی کانتینر
        - '3000:3000'
```
