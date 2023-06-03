##### RPC (Remote Procedure Call)
فراخوانی رویه‌ای دوردست
یک مدل برنامه‌نویسی است که اجازه می‌دهد که یک برنامه کلاینت درخواست از یک برنامه دیگر را از طریق شبکه و در دسترسی دور، ارسال کند.
##### gRPC (Google Remote Procedure Call)
کلاینت و سرور با استفاده از تعریف‌های پیش‌فرض و قراردادهای واسط  که با Protobuf تعریف می‌شوند، ارتباط برقرار می‌کنند. دیتا ها بصورت باینری ارسال می شودند بنابراین حجم دیتا ها پایین می آِد. بیشترین کاربردش برای میکروسرویس است.

#### Type of Services in gRPC
- Unary به معنا یگانه و مشابه rest است یعنی درخواست ارسال میشود و پاسخ دریافت می شود.
- Streaming ارسال و دریافت بصورت استریم و پی در پی
    - Server streaming سرور استریمی میفرستد
    - Client streaming کلاینت استریمی میفرستد
    - Unary streaming
    - Bidirectional streaming سرور و کلاینت استریمی رفتار میکنندف

#### Trailers
اطلاعاتی هستند که پس از ارسال محتوای اصلی پیام و قبل از بستن اتصال به عنوان بخشی از پیام ارسال می‌شوند. Trailers عبارتند از مجموعه‌ای از رئوس (headers) و مقادیر مربوط به آن‌ها که می‌توانند اطلاعاتی درباره پیام ارسالی اضافی (مانند خطاها یا وضعیت پاسخ) را دربرداشت کنند.
