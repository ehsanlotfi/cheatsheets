#### مشاهده دیتا تایپ ها و دیتاتایگ های غیر مجاز به ازای جداول
```
USE master
GO

SELECT * FROM INFORMATION_SCHEMA.COLUMNS
GO

SELECT * FROM INFORMATION_SCHEMA.COLUMNS
	WHERE DATA_TYPE IN('TEXT','NTEXT','IMAGE')
```
