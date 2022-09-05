#### مشاهده همه دیتا تایپ ها و دیتاتایپ های غیر مجاز به ازای جداول
```
USE master
GO

SELECT * FROM INFORMATION_SCHEMA.COLUMNS
GO

SELECT * FROM INFORMATION_SCHEMA.COLUMNS
	WHERE DATA_TYPE IN('TEXT','NTEXT','IMAGE')
```

#### بررسی ایندکس های جداول
```
EXEC sp_helpindex TableName
```

#### افزودن دستورات بصورت چندتایی
```
INSERT INTO Pet(Name, Animal) VALUES ('dog', 1)
go 20
```

#### بررسی حجم رکوردهای موجود در جداول
```
EXEC sp_spaceused TableName
```

#### بررسی وضعیت IO
```
SET STATISTICS IO ON 
SELECT * FROM Table1
SELECT * FROM Table2
SET STATISTICS IO OFF
GO
```
#### تکرار یک مقدار به تعداد مورد نظر
```
 select REPLICATE('hello', 1000)
```
