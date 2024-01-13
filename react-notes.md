### Handlle component Re render
- PureComponent and shouldComponentUpdate in Class component
- React.memo in function Component
  
برای اینکه ری‌رندر شدن یه کامپوننت رو کنترل کنیم
### shallow comparison
وقتی که props یا state در کامپوننت تغییر‌می‌کنه، PureComponent یه مقایسه سطحی روی props و state انجام میده به این عمل `shallow comparison`  میگن.

### Props vs State
- هر دو  javascript plain object  هستند Props شبیه به پارامترهای ورودی یک فانکشن، به کامپوننت پاس داده میشن در حالیکه state شبیه به متغییرهایی که داخل فانکشن ساخته شدن
##### Props
- ورودی های کامپوننت هستند
- - برای پاس دادن مقادیر به فرزند یا کامپوننت دیگر
##### State
- متغیر های درون یک کامپوننت و دیگر کامپوننت ها آن را نمی بینند.
