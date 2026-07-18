### Basic Neural Network Implementation

```python
import numpy as np
from tensorflow import keras
from tensorflow.keras import layers

# Input Features

X_train = np.array([
    [1,2,3,4,5,6,7,8,9,10],
    [2,3,4,5,6,7,8,9,10,11],
    [3,4,5,6,7,8,9,10,11,12],
    [4,5,6,7,8,9,10,11,12,13]
    ])

y_train = np.array([0,0,1,1])

X_test = np.array([[5,6,7,8,9,10,11,12,13,14]])


# 1. Define Model (layers, neurons, activation functions, input_shape)

model = keras.Sequential([
    layers.Dense(16, activation="relu", input_shape=(10,)), 
    layers.Dense(1, activation="sigmoid")
    ])

# 2. Compile Model (optimizer, loss function, evaluation metrics)

model.compile(optimizer="adam", loss="binary_crossentropy", metrics=["accuracy"])


# 3. Train Model ( epochs, batch size )

model.fit(X_train, y_train, epochs=10, batch_size=2)

# Predict (Inference)
prediction = model.predict(X_test)

```

---

### Activation functions

تابع فعال‌سازی مشخص می‌کند خروجی هر نورون چگونه محاسبه شود و باعث می‌شود شبکه عصبی بتواند روابط غیرخطی را یاد بگیرد.

- 1. ReLU (Rectified Linear Unit) `relu`
    - مقادیر بزرگ‌تر از صفر را بدون تغییر عبور می‌دهد و مقادیر کوچک‌تر از صفر را صفر می‌کند.
    - پرکاربردترین تابع فعال‌سازی در لایه‌های مخفی شبکه‌های عصبی است.

$$
f(x)=max(0,x)
$$


- 2. Sigmoid `sigmoid`
    - مقدار خروجی را بین 0 و 1 تبدیل می‌کند.
    - معمولاً در لایه خروجی مسائل Binary Classification استفاده می‌شود.

$$
f(x)=\frac{1}{1+e^{-x}}
$$


- 3. Tanh (Hyperbolic Tangent) `tanh` 
    - خروجی را بین -1 و 1 تبدیل می‌کند.
    - مشابه Sigmoid است اما خروجی آن حول صفر قرار دارد.

$$
f(x)=\frac{e^x-e^{-x}}{e^x+e^{-x}}
$$


- 4. Softmax `softmax`
    - خروجی چند نورون را به احتمال تبدیل می‌کند که مجموع آن‌ها برابر 1 است.
    - معمولاً برای مسائل Multi-Class Classification استفاده می‌شود.


- 5. Linear `linear`
    - خروجی را بدون تغییر عبور می‌دهد.
    - معمولاً در خروجی مسائل Regression استفاده می‌شود.

$$
f(x)=x
$$


---

### Optimizer functions

مشخص می‌کند وزن‌های شبکه عصبی چگونه با استفاده از گرادیان و خطا به‌روزرسانی شوند.

- 1. SGD (Stochastic Gradient Descent) `optimizer=keras.optimizers.SGD(learning_rate=0.01)`
    - وزن‌ها را با استفاده از گرادیان خطا تغییر می‌دهد.
    - ساده‌ترین الگوریتم بهینه‌سازی است.
    - برای دیتاست‌های بزرگ مناسب است.

$$
W_{new}=W_{old}-\eta \nabla L(W)
$$


- 2. SGD + Momentum `optimizer=keras.optimizers.SGD(learning_rate=0.01, momentum=0.9)`
    - علاوه بر گرادیان فعلی، حرکت‌های قبلی را نیز در نظر می‌گیرد.
    - باعث کاهش نوسان و سریع‌تر شدن یادگیری می‌شود.

- 3. SGD + Nesterov Momentum (NAG) `keras.optimizers.SGD(learning_rate=0.01, momentum=0.9, nesterov=True)`
    - نسخه پیشرفته‌تر Momentum است.
    - قبل از محاسبه گرادیان، یک قدم به جلو نگاه می‌کند و سپس مقدار خطا را اصلاح می‌کند.
    - معمولاً نسبت به Momentum معمولی مسیر دقیق‌تری برای رسیدن به نقطه بهینه پیدا می‌کند.

$$
v_t=\beta v_{t-1}+\nabla L(W_t-\eta\beta v_{t-1})
$$

$$
W_{t+1}=W_t-\eta v_t
$$

- 4. RMSprop `optimizer=keras.optimizers.RMSprop(learning_rate=0.001)`
    - نرخ یادگیری را برای هر وزن به صورت جداگانه تنظیم می‌کند.
    - برای شبکه‌های عصبی بازگشتی (RNN) کاربرد زیادی دارد.


- 5. Adam (Adaptive Moment Estimation) `optimizer=keras.optimizers.Adam(learning_rate=0.001)`
    - ترکیبی از Momentum و RMSprop است.
    - به صورت خودکار نرخ یادگیری مناسب را تنظیم می‌کند.
    - یکی از رایج‌ترین Optimizerها در Deep Learning است.


- 6. AdamW `optimizer=keras.optimizers.AdamW(learning_rate=0.001, weight_decay=0.004)`
    - نسخه بهبود یافته Adam است که Weight Decay را بهتر مدیریت می‌کند.
    - برای مدل‌های بزرگ مانند Transformerها کاربرد زیادی دارد.


---

### Loss functions

میزان اختلاف بین خروجی مدل و مقدار واقعی را اندازه‌گیری می‌کند. هدف آموزش شبکه، کمینه کردن مقدار Loss است.

- 1. Mean Squared Error (MSE) `mse`
    - میانگین مربع اختلاف بین مقدار پیش‌بینی‌شده و مقدار واقعی است.
    - مناسب برای مسائل Regression.

$$
MSE=\frac{1}{n}\sum(y-\hat{y})^2 ``
$$


- 2. Mean Absolute Error (MAE) `mae`
    - میانگین قدر مطلق اختلاف بین مقدار واقعی و پیش‌بینی‌شده است.
    - نسبت به خطاهای بزرگ حساسیت کمتری دارد.

$$
MAE=\frac{1}{n}\sum |y-\hat{y}|
$$


- 3. Binary Crossentropy `binary_crossentropy`
    - برای مسائل دوکلاسه استفاده می‌شود.
    - احتمال پیش‌بینی‌شده را با کلاس واقعی مقایسه می‌کند.

- 4. Categorical Crossentropy `categorical_crossentropy`
    - برای مسائل چندکلاسه استفاده می‌شود.
    - زمانی که برچسب‌ها به صورت One-Hot Encoding باشند.


- 5. Sparse Categorical Crossentropy `sparse_categorical_crossentropy`
    - مشابه Categorical Crossentropy است.
    - تفاوت آن در این است که برچسب‌ها به صورت عددی هستند.



---

### Metrics

Metrics معیارهایی هستند که عملکرد مدل را هنگام آموزش و ارزیابی اندازه‌گیری می‌کنند.
Metric روی یادگیری مدل تأثیر ندارد و فقط برای گزارش عملکرد استفاده می‌شود.

- 1. Accuracy `accuracy`
    - درصد پیش‌بینی‌های صحیح مدل را نشان می‌دهد.

$$
Accuracy=\frac{Correct\ Predictions}{Total\ Predictions}
$$


- 2. Precision `Precision`
    - از بین نمونه‌هایی که مدل مثبت پیش‌بینی کرده، چند مورد واقعاً مثبت بوده‌اند.

$$
Precision=\frac{TP}{TP+FP}
$$


- 3. Recall (Sensitivity) `Recall`
    - از بین نمونه‌های مثبت واقعی، چند مورد توسط مدل شناسایی شده‌اند.

$$
Recall=\frac{TP}{TP+FN}
$$


- 4. F1-Score `metrics=[keras.metrics.F1Score()]`
    - میانگین هماهنگ Precision و Recall است.
    - برای داده‌های نامتوازن مناسب است.

$$
F1=2\times\frac{Precision \times Recall}{Precision+Recall}
$$


- 5. AUC (Area Under Curve) `AUC`
    - توانایی مدل برای جدا کردن کلاس‌ها را اندازه‌گیری می‌کند.
    - مقدار نزدیک به 1 نشان‌دهنده مدل بهتر است.