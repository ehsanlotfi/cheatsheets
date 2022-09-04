<div dir="rtl">
مشاهده دیتا تایپ ها و دیتاتایگ های غیر مجاز به ازای جداول
</div>

مکمنئبیلنئنئ  منتئیمبل 

```
USE master
GO
--مشاهده دیتا تایپ ها به ازای جداول
SELECT * FROM INFORMATION_SCHEMA.COLUMNS
GO
--مشاهده دیتا تایپ های غیر مجاز
SELECT * FROM INFORMATION_SCHEMA.COLUMNS
	WHERE DATA_TYPE IN('TEXT','NTEXT','IMAGE')
GO
```
