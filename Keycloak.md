## KeyCloak

یک راه حل برای مدیریت ، امنیت و اعمال دسترسی برای برنامه های تحت وب می باشد که به صورت RESTful می توان از آن در پروژه های مختلف اعم از client-side  و   server-side استفاده نمود.

این برنامه قادر است برای ما مدیریت کاربران را برعهده گرفته و با امکاناتی که در آن قرار گرفته است خیال ما را از بابت امنیت و اعطای دسترسی به کاربران راحت نموده .

 ### از جمله امکاناتی که این برنامه قادر به پیاده سازی آن می باشد شامل :
-	Standard Protocols (OpenID Connect, OAuth 2.0 and SAML 2.0)
-	Single-Sign On
-	LDAP and Active Directory
-	Clustering
-	Social Login
-	Password Policies
-	Admin Console
-	Account Management
-	Authorization Services
-	Open Source
-	Multi Platform (Docker, Kubernetes, Windows)

### آدرس روی گیت : 
https://github.com/keycloak/keycloak

### داشبورد KeyCloak
قبل شروع به توضیح کار با داشبورد این برنامه ، لازم است که چند مفاهیم اصلی و اصطلاحات اصلی در این برنامه را فرا بگیرید :

-	User : کاربران موجودیت هایی هستند که قادر به ورود به سیستم هستند و ویژگی های مرتبط با خود مانند ایمیل، نام کاربری، آدرس، شماره تلفن و تاریخ تولد را داشته باشند. می توان به آنها عضویت گروه اختصاص داد و همچنین نقش های خاصی را به آنها تخصیص داد.
-	Authentication : فرآیند شناسایی و اعتبار سنجی یک کاربر.
-	Authorization : فرآیند اعطای دسترسی به کاربر.
-	Roles : نقش ها نوع یا دسته ای از کاربر را مشخص می کند.(مدیر، کاربر، کارمند و...)
-	User Role  Mapping : تخصیص میان نقش و کاربر را تعریف می کند. Role Mapping را میتوان در Tokens و assertions  کپسوله کرد تا برنامه ها مجوزهای دسترسی را در منابع مختلفی که مدیریت می کنند تصمیم بگیرند. (امکان تعریف نقش های ترکیبی به عنوان مثال نقش های مدیریت فروش و مدیر ورود سفارش )
-	Groups : می توان نقش ها را به یک گروه خاص تخصیص داد. کاربرانی که عضو یک گروه می شوند ویژگی ها و نگاشت نقش هایی را که گروه دارد را به ارث می برند.
-	Realms : یک قلمرو و مجموعه از کاربران ، اعتبارنامه ها(Credentials)، نقش ها و گروه ها را مدیریت می کند. کاربر به یک قلمرو تعلق دارد و وارد آن می شود. قلمرو ها از یکدیگر جدا هستند و فقط می توانند کاربرانی را که کنترل می کنند مدیریت و احراز هویت کنند.
-	 : Clientsموجودیت هایی که می توانند از KeycLoak برای احراز هویت یک کاربر درخواست کنند. اغلب Clients برنامه ها و سرویس هایی هستند که می خواهند از Keycloak برای ایمن کردن خود و از یک Single sign-on استفاده کنند.
Clients ها همچنین می توانند موجودیت هایی باشند که فقط می خواهند اطلاعات هویتی یا یک دسترسی را درخواست کنند تا بتوانند به طور ایمن خدمات دیگیری را در شبکه که توسط Keycloak ایمن شده اند فراخوانی کنند.
-	Client Adapters : پلاگین های هستند که در محیط برنامه نصب می کنید تا بتوانید با Keycloak ارتباط برقرار کنید و ایمن شوند. Keycloak تعداد آداپتور برای پلتفرم های مختلف دارد که می توان آنها را دانلود کرد .
-	Scope : به معنی محدوده ، هنگامی که یک Client ثبت می شود، باید  پروتکل و نقش های مورد نظر را برای آن Client تعریف نمود. توصیه می شود scope کاربر را ذخیره کرد تا با به اشتراک گذاشتن برخی تنظیمات مشترک ایجاد Clients جدید را آسان تر نمود. همچنین میتوان برای درخواست برخی Claims و یا نقش ها که به صورت مشروط براساس مقدار پارامتر Scope باشد .
-	Token : Access Token  که می تواند به عنوان بخشی از درخواست HTTP ارایه شود و به سرویسی که در حال فراخوانی است دسترسی می دهد. این بخشی از مشخصات OpenId Connect  و Oauth2.0 است.
-	Service Account : هر Client دارای یک حساب سرویس داخلی(Build-in) است که به آن امکان می دهد یک Access Token به دست آورد.
-	Session : هنگامی که یک کاربر وارد سیستم می شود، یک Session برای مدیریت Session ایجاد می شود. یک Session حاوی اطلاعاتی مانند زمان ورود کاربر و چه برنامه هایی است که در طی آن Session در یک ورود به سیستم شرکت کرده اند. (ادمین و کاربران می توانند اطلاعات Session را مشاهده کنند).
-	User Federation Provider : بسیاری از شرکت ها قبلا از سرویس LDAP یا Active Directory استفاده می کنند که اطلاعات کاربر و مجوز دسترسی را درون خود ذخیره می کنند. میتوان به Keycloak اشاره (استفاده نمود)کرد تا Credentials (اعتبارنامه های) ذخیره خارجی را تایید کند و اطلاعات هویتی را دریافت کند.
-	IDP : Identity Provider ارایه دهنده هویت سرویسی است که می تواند یک کاربر را احراز هویت کند.
-	Authentication Flows : جریان های کاری هستند که کاربر باید هنگام تعامل با جنبه های خاصی از سیستم انجام دهد. این جریان ها مشخص می کنند که کاربر باید چه اطلاعاتی را وارد کند و آیا چیزی همانند reCAPTCHA باید برای فیلتر کردن ربات ها استفاده شود یا خیر . همچنین سیاست هایی برای تغییر رمز عبور (بازنشانی) صورت می گیرد.
-	Events : رویدادها جریان های حسابرسی هستند که مدیران می توانند آن ها را مشاهده کرده و به آنها متصل شوند.
-	Themes : هر صفحه نمایش ارایه شده توسط Keycloak توسط یک موضوع پشتیبانی می شود. تم ها قالب ها و شیوه نامه های HTML را تعریف می کنند که می توانید در صورت نیاز آن ها را غیر فعال کنید.
این تعاریف فوق مهمترین تعاریف بخش مربوط به Keycloak می باشد که قبلا از استفاده ، میبایست با آنها آشنا باشید که بتوانی به راحتی از داشبورد برنامه استفاده کنید.
در تصویر زیر نمای کلی از داشبورد برنامه در نسخه 20.0.3 را مشاهده می کنید :
 
با توجه به اینکه در شرکت نیاز بر پیاده سازی sso می باشد به همین دلیل در ابتدا می بایست یک Realm به صورت عمومی تعریف کنید که در داخل آن کلیه سامانه ها و برنامه هایی که نیاز داریم برای آنها احرازهویت انجام بشود ،

 در بخش Client تعریف می کنید ، پس از آن برای این بخش(Client) شروع به تعریف Role خواهیم کرد ، دلیل این امر آن است که ارتباط کاربران با این سامانه ها از طریق همین Role صورت میگیرد.

پس از تعریف Role ها اقدام به تعریف User ها می کنیم ، در این بخش بعد از تعریف کاربر و اعطای کلمه عبور برای آنها اقدام به انتصاب کاربر به Role تعریف شده در بخش Client می کنیم 

نکته قابل توجه آن است که می توان یک گروه برای کاربران تعریف کرد که کاربران به آن گروه ها ملحق شده و تمامی تنظیماتی که در آن گروه اعمال شده ، شامل Role،   Attributeو غیره به کاربران اتصاب داده خواهد شد . 

بخش مربوط به ClientScope مربوط به قلمروی سامانه ها می باشد و مهمترین اقدامی که میشود در این بخش انجام داد ، تنظیم مقادیر مورد نظر جهت قرار گرفتن درون Token  می باشد ، پس از تعریف این بخش می توان آن را به Client انتصاب داد ، سپس سامانه ها از تنظیمات موجود درون آن استفاده کرده و بر روی آنها اعمال خواهد شد.

