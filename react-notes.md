### Virtual DOM
مفهومیه که توسط کتابخونه‌ها مثل ریاکت برای مدیریت DOM توسط جاواسکریپت با استفاده از APIهای مرورگرها اجرا شده.در سه مرحله ایجاد می شود.
- هر زمان که داده‌های اساسی تغییر ‌می‌کنن، کل رابط کاربری توسط DOM مجازی مجددا رندر میشه.
- تفاوت بین DOM قبلی و جدید محاسبه میشه.
- بعد از انجام محاسبات، DOM واقعی فقط با مواردی که واقعاً تغییر کردن به روز میشه.
### Reconciliation
به معنای لغوی اصلاح وقتی state‌ یا props یه کامپوننت تغییر‌می‌کنه، ری‌اکت با مقایسه عنصر تازه return شده و نمونه render شده قبلی تصمیم میگیره که به روزرسانی DOM واقعا ضروریه یا نه. وقتی این دو مقدار با هم برابر نباشه، ری‌اکت به روزرسانی DOM رو انجام میده. به این فرایند reconciliation گفته میشه.

### React Fiber
موتور جدید برای عملیات reconciliation هست یا میشه گفت که پیاده‌سازی مجدد الگوریتم هسته ری‌اکت نسخه ۱۶ هست. هدف پیاده‌سازی ReactFiber برای بهبود کارکرد توی جاهایی مثل ایجاد انیمیشن، کار روی layout، کار با gestureها و قابلیت اینکه عملیات در حال اجرا رو متوقف، قطع یا مجددا فعال کنیم ساخته شده. البته می‌تونه برای اولویت‌بندی بروزسانی‌های لازم توی DOM رو هم مدیریت کنه. مهم‌ترین ویژگی incremental-rendering بوده که قابلیت بخش‌بندی(chunk کردن) عملیات اجرایی و متوقف و اجرا کردن اون توی فریم‌های مختلف هست.
### set state for dynamic Model
```
const [myState, setMyState] = useState();
const handleInputChange = (event) => {
  setMyState({ [event.target.id]: event.target.value });
}
```

### lifecycle Class Component
- Mounting `constructor,  getDerivedStateFromProps,  render,  componentDidMount`
- Updating `getDerivedStateFromProps, shouldComponentUpdate,  render,  getDerivedStateFromProps,  componentDidUpdate`
- Unmounting `componentWillUnmount`

### lifecycle phases
- Render
- Pre-commit
- Commit

### HOC ( Hight Order Component )
کامپوننت با مرتبه بالا
در واقع یک تابع است که یک کامپوننت را به عنوان ورودی می‌گیرد و یک کامپوننت جدید با ویژگی‌ها یا عملکردهای جدید به عنوان خروجی برمی‌گرداند. برای مثال، فرض کنید شما یک کامپوننت دارید که اطلاعات  یک فرد را نمایش می‌دهد، و شما می‌خواهید این اطلاعات را بر اساس سن فرد تغییر دهید. می‌توانید یک HOC بنویسید که با توجه به سن افراد، ویژگی‌های مختلفی به کامپوننت اضافه کند.
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
### props proxy in HOC
می‌تونیم prop‌های انتقال داده شده به کامپوننت رو با استفاده از الگوی props proxy اضافه یا ویرایش کنیم:
```
function HOC(WrappedComponent) {
  return class Test extends Component {
    render() {
      const newProps = {
        title: "New Header",
        footer: false,
        showFeatureX: false,
        showFeatureY: true,
      };

      return <WrappedComponent {...this.props} {...newProps} />;
    }
  };
}
```

### context
برای انتقال اطلاعات بین کامپوننت ها 
``` const { Provider, Consumer } = React.createContext(defaultValue); ```

### Fragment
استفاده چندین المنت بدون افزودن نود اضافی
```
render() {
  return (
    // First type
    <React.Fragment>
      <ChildA />
      <ChildB />
    </React.Fragment>

   // Second type
    <>
        <ChildA />
        <ChildB />
      </>
  )
}

### portal in React
روشی توصیه شده برای رندر کردن کامپوننت فرزند به شکل DOM و خارج از سلسله مراتب DOM کامپوننت والد هستش. اولین آرگومان یه فرزند قابل رندر شدن هستش، مثل عنصر، رشته، یا fragment. آرگومان دوم عنصر DOM هستش.

```
ReactDOM.createPortal(child, container);
```

```
### NOTES
- اگر `state` را مستقیم آپدیت کنیم کامپوننت ما ری رندر نمی شود.
- متدهای `Callback` در ریاکت معمولا به عنوان پارمترهای دوم هوکس ها می آیند و بعد از عملیات هوکس می شود کاری انجام داد.
```
setState({ name: "John" }, () =>
  console.log("The name has updated and component re-rendered")
)
```
