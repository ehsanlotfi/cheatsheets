از چه ایمجی استفاده کنه
```
FROM rocksolidknowledge/identityserver-dev-sso
```
کپی کردن استارت آپ به استارت آپ جاری ایمیج
```
COPY startup.sh /
```
بعد از اجرای کانتینر چه فایلی اجرا شود
```
ENTRYPOINT [ "/startup.sh" ]
```
