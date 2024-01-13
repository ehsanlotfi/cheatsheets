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

### Events in React and HTML
- تعریف ایونت در HTML بصورت loverCase است و در react بصورت camelCase
- توی HTML برای جلوگیری از رفتار پیش فرض می تونیم return کنیم ولی در react حتما باید PreventDefault استفاده بشه
- در HTML حتما باید پرانتز ها گذاشته شود در React اجباری نیست.
```
// HTML
<button onclick="activateLasers()"></button>
<a href="#" onclick='console.log("The link was clicked."); return false;' />

// React
<button onClick={activateLasers}>Test</button>
function activateLasers(event) {
  event.preventDefault();
}
```
### Synthetic events
رویدادهای مصنوعی یه رخداد cross-browser هست که به‌عنوان یه wrapper دور eventهای اصلی مرورگر قرار می‌گیره. رابط API برای کارکردن با اون دقیقا مثل رخداد native مرورگرهاست که شامل stopPropagation و preventDefault میشه، با این تفاوت که این رخداد‌ها بر روی همه مرورگرها کار می‌کنن.

### Ref and ForwardRef
در کلاس کامپوننت از React.createRef() استفاده میکنیم و در فانکشن کامپوننت از هوکس userRef 
مفهوم Ref forwarding ویژگی‌ایه که به بعضی از کامپوننت‌ها این اجازه رو میده ref دریافت شده رو به کامپوننت فرزند انتقال بدن.

### NOTES
- اگر `state` را مستقیم آپدیت کنیم کامپوننت ما ری رندر نمی شود.
- متدهای `Callback` در ریاکت معمولا به عنوان پارمترهای دوم هوکس ها می آیند و بعد از عملیات هوکس می شود کاری انجام داد.
```
setState({ name: "John" }, () =>
  console.log("The name has updated and component re-rendered")
)
```
