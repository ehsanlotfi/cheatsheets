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
#### GHOST CLEANUP مشاهده پروسه 
```
DECLARE @Gh NVARCHAR(1000)=''
DECLARE @ST DATETIME
WHILE (@Gh='')
BEGIN
		SELECT @Gh=command ,@ST=start_time From sys.dm_exec_requests Where COMMAND like '%GHOST%';
End
SELECT  @Gh
SELECT  @ST
GO
```

### حذف بانک اطلاعاتی
```
IF DB_ID('TestDatabase')>0
BEGIN
	ALTER DATABASE TestDatabase SET SINGLE_USER WITH ROLLBACK IMMEDIATE
	DROP DATABASE TestDatabase
END
GO
```
#### استخراج پیج های متعلق به جدول
```
DBCC IND(TestDatabase, DeleteInternals, 1) 
DBCC TRACEON(3604)
GO
```
#### Page Header در m_ghostRecCnt,m_slotCnt بررسی
```
DBCC PAGE(TestDatabase, 1,292,2) 
GO
```

