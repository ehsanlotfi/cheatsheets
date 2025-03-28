 #### 𝐓𝐨𝐩 𝐌𝐚𝐜𝐡𝐢𝐧𝐞 𝐋𝐞𝐚𝐫𝐧𝐢𝐧𝐠 𝐀𝐥𝐠𝐨𝐫𝐢𝐭𝐡𝐦𝐬:
 ##### 1- K-Means Clustering
ابتدا تعداد خوشه‌ها (K) را مشخص می‌کنیم. سپس، K نقطه را به‌عنوان مراکز اولیه انتخاب کرده و هر داده را به نزدیک‌ترین مرکز نسبت می‌دهیم. بعد از آن، میانگین نقاط هر گروه را محاسبه کرده و مرکز خوشه را به‌روزرسانی می‌کنیم. این مراحل را تکرار می‌کنیم تا دیگر تغییری در مراکز خوشه‌ها ایجاد نشود. در نهایت، داده‌ها در K گروه مشابه دسته‌بندی می‌شوند.
##### 2- Linear Regression
خود رگرسیون به معنای پیش بینی تغییرات یک متغیر به توجه به تغییرات متغیر دیگر است. فرمول رگرسیون خطی به شرح زیر است.
###### `y = ( m × x ) + b`
- y → مقدار پیش‌بینی‌شده
- x → متغیر مستقل (ورودی)
- m → شیب خط (میزان تأثیر x بر y)
- b → عرض از مبدأ (مقدار y وقتی x صفر است)

##### 3- Decision Tree
درخت تصمیم یک مدل یادگیری ماشین است که با استفاده از یک سری پرسش‌های بله/خیر یا مقایسه‌ای، داده‌ها را دسته‌بندی یا پیش‌بینی می‌کند.

![1733588394092](https://github.com/user-attachments/assets/6f50b4a7-74b3-49b7-b6b1-d9982cc79b6b)

#### Digital twin
دوقلو دیجیتال، نسخه‌ای دیجیتال از یک شیء یا سیستم فیزیکی یا یک ساختار فیزیکی (کارخانه، دیتاسنتر، کره زمین، حرم) است که به ما امکان مشاهده و تحلیل آن در زمان واقعی را می‌دهد. پروژه Earth 2
#### Unconditional Image Generation
توضیح: مدل‌هایی که بدون نیاز به ورودی مشخص، تصاویر جدیدی تولید می‌کنند.
مثال: مدلی مثل GAN که تصاویر جدید از چهره‌های انسان‌ها تولید می‌کند بدون اینکه ورودی خاصی دریافت کند.
#### Depth Estimation
توضیح: مدل‌هایی که از تصاویر دو بعدی، اطلاعات عمق (سه بعدی) تخمین می‌زنند.
مثال: فرض کنید تصویری از یک جاده دارید، مدل عمق اشیاء مختلف مثل ماشین‌ها و درختان را تخمین می‌زند.
#### Zero-Shot Image Classification
توضیح: مدل‌هایی که می‌توانند تصاویر را بدون آموزش مستقیم روی آن دسته‌ها، دسته‌بندی کنند.
مثال: اگر مدل روی دسته‌های "سگ" و "گربه" آموزش دیده باشد، ولی تصویر "فیل" را دسته‌بندی کند بدون اینکه قبلا آموزشی درباره "فیل" دیده باشد.
#### Zero-Shot Object Detection
توضیح: مدل‌هایی که بدون دیدن نمونه‌های خاص از یک شیء، قادر به تشخیص آن در تصاویر هستند.
مثال: مدل قبلا روی شناسایی "ماشین" و "دوچرخه" آموزش دیده ولی حالا می‌تواند "اتوبوس" را بدون آموزش مستقیم تشخیص دهد.

#### Token Classification
توضیح: مدل‌هایی که هر کلمه یا توکن در یک جمله را به یک دسته خاص نسبت می‌دهند.
مثال: در یک جمله مثل "علی به مدرسه رفت"، مدل می‌تواند "علی" را به عنوان "اسم" و "مدرسه" را به عنوان "مکان" دسته‌بندی کند.
#### Table Question Answering
توضیح: مدل‌هایی که به سوالات درباره داده‌های جدول‌ها پاسخ می‌دهند.
مثال: شما یک جدول از فروش محصولات دارید و سوال می‌پرسید "چه محصولی بیشترین فروش را داشت؟" و مدل پاسخ می‌دهد.

#### Fill-Mask
توضیح: مدل‌هایی که کلمات گمشده در یک جمله را پر می‌کنند.
مثال: جمله "هوا [MASK] است" را به مدل می‌دهید و مدل آن را به "هوا آفتابی است" تکمیل می‌کند.
#### Voice Activity Detection
توضیح: مدل‌هایی که تشخیص می‌دهند در چه بخش‌هایی از یک فایل صوتی، گفتار وجود دارد.
مثال: مدلی که در یک فایل صوتی بلند، بخش‌هایی که شامل صحبت‌های یک فرد است را شناسایی می‌کند.
#### Tabular Classification
توضیح: مدل‌هایی که داده‌های جدولی را بر اساس دسته‌های مختلف دسته‌بندی می‌کنند.
مثال: مدلی که داده‌های مشتریان را به دسته‌های "خریدار وفادار" و "خریدار معمولی" دسته‌بندی می‌کند.
#### Tabular Regression
توضیح: مدل‌هایی که پیش‌بینی مقدارهای پیوسته بر اساس داده‌های جدولی انجام می‌دهند.
مثال: مدلی که بر اساس ویژگی‌های خانه مثل اندازه و موقعیت، قیمت آن را پیش‌بینی می‌کند.
#### Time Series Forecasting
توضیح: مدل‌هایی که روندهای آینده را بر اساس داده‌های زمانی پیش‌بینی می‌کنند.
مثال: مدلی که پیش‌بینی می‌کند قیمت سهام در ماه آینده چگونه تغییر خواهد کرد.

#### Reinforcement Learning
توضیح: مدل‌هایی که از طریق پاداش و تنبیه یاد می‌گیرند که چگونه وظایف را بهتر انجام دهند.
مثال: مدلی که یک ربات را آموزش می‌دهد که چگونه در یک ماز حرکت کند تا به هدف برسد.

#### Model Distillation 
یک تکنیک در یادگیری ماشین است که برای فشرده‌سازی مدل‌های بزرگتر (معمولاً پیچیده و سنگین) به مدل‌های کوچکتر (ساده‌تر و سبک‌تر) استفاده می‌شود، بدون اینکه دقت زیادی از دست برود. در این فرآیند، یک مدل بزرگ (که به آن "مدل معلم" گفته می‌شود) ابتدا آموزش داده می‌شود، سپس اطلاعات آن مدل به یک مدل کوچکتر (مدل "دانش‌آموز") منتقل می‌شود. هدف این است که مدل دانش‌آموز از خروجی‌های مدل معلم یاد بگیرد و بتواند عملکرد مشابهی با آن ارائه دهد، اما با منابع محاسباتی کمتر و سرعت بالاتر.

#### Model Collapse
فروپاشی مدل پدیده‌ای است که در مدل‌های مولد مانند GANها رخ می‌دهد و باعث می‌شود مدل به جای تولید خروجی‌های متنوع، به تولید نمونه‌های مشابه یا یکسان محدود شود. این اتفاق زمانی می‌افتد که مدل نتواند توزیع گسترده داده‌های ورودی را به‌درستی یاد بگیرد و فقط به تولید یک بخش کوچک و محدود از آن توزیع بپردازد، که منجر به کاهش کیفیت و تنوع خروجی‌های تولید شده می‌شود. و مدل خروجی ها مشابه دارد.

#### Mixture of Experts (MoE)
سوال وارد مدل زبانی میشه و در گام اول تخصیص داده میشه به واحد پردازشی متخصص مورد نظرش

#### Fine-Tune
فاین‌تیونینگ  به معنای تنظیم دقیق یا تربیت مجدد مدل روی یک مجموعه داده خاص است.
