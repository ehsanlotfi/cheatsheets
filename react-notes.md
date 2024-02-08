### Virtual DOM
مفهومی که توسط کتابخونه‌ها مثل ریاکت برای مدیریت `DOM` توسط جاواسکریپت با استفاده از `API` های مرورگرها اجرا شده.در سه مرحله ایجاد می شود.
- هر زمان که داده‌های اساسی تغییر ‌می‌کنن، کل رابط کاربری توسط `DOM` مجازی مجددا رندر میشه.
- تفاوت بین `DOM` قبلی و جدید محاسبه میشه.
- بعد از انجام محاسبات، `DOM` واقعی فقط با مواردی که واقعاً تغییر کردن به روز میشه.



### Props vs State
- هر دو  javascript plain object  هستند `Props` شبیه به پارامترهای ورودی یک فانکشن، به کامپوننت پاس داده میشن در حالیکه `state` شبیه به متغییرهایی که داخل فانکشن ساخته شدن
##### Props
- ورودی های کامپوننت هستند
- برای پاس دادن مقادیر به فرزند یا کامپوننت دیگر
- بصورت immutable و تغییر ناپذیر برای فرزندان هستند و فقط از طریق پدر باید آپدیت شوند
##### State
- متغیر های درون یک کامپوننت و دیگر کامپوننت ها آن را نمی بینند.

### Events in React and HTML
- تعریف ایونت در HTML بصورت loverCase است و در `react` بصورت `camelCase`
- توی `HTML` برای جلوگیری از رفتار پیش فرض می تونیم return کنیم ولی در `react` حتما باید `PreventDefault` استفاده بشه
- در `HTML` حتما باید پرانتز ها گذاشته شود در `React` اجباری نیست.
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




### Reconciliation
به معنای لغوی اصلاح وقتی `state‌` یا `props` یه کامپوننت تغییر‌می‌کنه، ری‌اکت با مقایسه عنصر تازه return شده و نمونه `render` شده قبلی تصمیم میگیره که به روزرسانی `DOM` واقعا ضروریه یا نه. وقتی این دو مقدار با هم برابر نباشه، ری‌اکت به روزرسانی `DOM` رو انجام میده. به این فرایند `reconciliation` گفته میشه.



### React Fiber
موتور جدید برای عملیات `reconciliation` هست یا میشه گفت که پیاده‌سازی مجدد الگوریتم هسته ری‌اکت نسخه ۱۶ هست. هدف پیاده‌سازی `ReactFiber` برای بهبود کارکرد توی جاهایی مثل ایجاد انیمیشن، کار روی `layout،` کار با gestureها و قابلیت اینکه عملیات در حال اجرا رو متوقف، قطع یا مجددا فعال کنیم ساخته شده. البته می‌تونه برای اولویت‌بندی بروزسانی‌های لازم توی DOM رو هم مدیریت کنه. مهم‌ترین ویژگی `incremental-rendering` بوده که قابلیت بخش‌بندی(chunk کردن) عملیات اجرایی و متوقف و اجرا کردن اون توی فریم‌های مختلف هست.


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



#### getDerivedStateFromProps
بعد از اینکه یه کامپوننت بلافاصله بدون خطا و مثل قبل `rerender` شد، متد استاتیک `getDerivedStateFromProps` صدا زده میشه.
این متد یا `state` آپدیت شده رو به صورت یه آبجکت برمی گردونه یا `null` رو برمی گردونه که معنیش اینه `prop` ‌های جدید به آپدیت شدن `state` نیازی ندارن.
```
class MyComponent extends React.Component {
  static getDerivedStateFromProps(props, state) {
    //...
  }
}
```



#### getSnapshotBeforeUpdate
بعد از آپدیت‌های `DOM` صدا زده میشه.
مقدار برگشتی این متد به عنوان پارامتر سوم به متد `componentDidUpdate` پاس داده میشه.
```
class MyComponent extends React.Component {
  getSnapshotBeforeUpdate(prevProps, prevState) {
    //...
  }
}
```
متد `componentDidUpdate` تمام مواردی که توی متد `componentWillUpdate`, `componentWillReceiveProps` استفاده میشه رو پوشش میده.



### HOC ( Hight Order Component )
کامپوننت با مرتبه بالا
در واقع یک تابع است که یک کامپوننت را به عنوان ورودی می‌گیرد و یک کامپوننت جدید با ویژگی‌ها یا عملکردهای جدید به عنوان خروجی برمی‌گرداند. برای مثال، فرض کنید شما یک کامپوننت دارید که اطلاعات  یک فرد را نمایش می‌دهد، و شما می‌خواهید این اطلاعات را بر اساس سن فرد تغییر دهید. می‌توانید یک `HOC` بنویسید که با توجه به سن افراد، ویژگی‌های مختلفی به کامپوننت اضافه کند.



### Handlle component Re render
- PureComponent and shouldComponentUpdate in Class component
- React.memo in function Component
  
برای اینکه ری‌رندر شدن یه کامپوننت رو کنترل کنیم



### shallow comparison
وقتی که `props` یا `state` در کامپوننت تغییر‌می‌کنه، `PureComponent` یه مقایسه سطحی روی `props` و `state` انجام میده به این عمل `shallow comparison`  میگن.



### Synthetic events
رویدادهای مصنوعی یه رخداد `cross-browser` هست که به‌عنوان یه `wrapper` دور eventهای اصلی مرورگر قرار می‌گیره. رابط API برای کارکردن با اون دقیقا مثل رخداد native مرورگرهاست که شامل `stopPropagation` و `preventDefault` میشه، با این تفاوت که این رخداد‌ها بر روی همه مرورگرها کار می‌کنن.



### Ref and ForwardRef
در کلاس کامپوننت از `React.createRef()` استفاده میکنیم و در فانکشن کامپوننت از هوکس `userRef` 
مفهوم `Ref forwarding` ویژگی‌ایه که به بعضی از کامپوننت‌ها این اجازه رو میده ref دریافت شده رو به کامپوننت فرزند انتقال بدن.



### props proxy in HOC
می‌تونیم prop‌های انتقال داده شده به کامپوننت رو با استفاده از الگوی `props proxy` اضافه یا ویرایش کنیم:
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
```



### portal in React
روشی توصیه شده برای رندر کردن کامپوننت فرزند به شکل `DOM` و خارج از سلسله مراتب `DOM` کامپوننت والد هستش. اولین آرگومان یه فرزند قابل رندر شدن هستش، مثل عنصر، رشته، یا `fragment`. آرگومان دوم عنصر `DOM` هستش.
```
ReactDOM.createPortal(child, container);
```




#### PropType
در محیط توسعه کاربرد دارد برای مشخص کردن نوع ووردی یک کامپوننت
با استفاده از typescript هم میتوان `type checking` داشت
```
import React from "react";
import PropTypes from "prop-types";

const User = (props) => {
  return (
    <>
      <h1>{`Welcome, ${props.name}`}</h1>
      <h2>{`Age, ${props.age}`}</h2>
    </>
  );
}

User.propTypes = {
  name: PropTypes.string.isRequired,
  age: PropTypes.number.isRequired,
};
```



### error boundary
در کلاس کامپوننت کارایی دارد و با متد هایی مانند `componentDidCatch(error, info)`  و `static getDerivedStateFromError` . پیاده سازی می شود.
از این در فانکشن کامپوننت نمیشه استفاده کرد و نیازی هم بهش نداریم چون اکثر مواقع برای کل برنامه یه `error boundary` تعریف می‌کنیم که می‌تونه `try..catch` باشه.




### Memoize 
به معنا حفظ کردن قبلا بوسیله کتابخونه های خارجی انجام میشد ولی از نسخه 16 به بعد از React.memo  استفاده می شود.
```
export default React.memo(MyFunctionComponent);
```

### SSR in pure React
```
import ReactDOMServer from "react-dom/server";
import App from "./App";

ReactDOMServer.renderToString(<App />);
```

### Ordering Style Guide in React
1. static
1. constructor
1. getChildContext
1. componentWillMount
1. componentDidMount
1. componentWillReceiveProps
1. shouldComponentUpdate
1. componentWillUpdate
1. componentDidUpdate
1. componentWillUnmount
1. event handler (onClick, onChange , ...)
1. render methods


### Switcher Component
کامپوننتی که توسط شروطی چند تا کامپوننت را میتواند رندر کند
```
import HomePage from "./HomePage";
import AboutPage from "./AboutPage";

const PAGES = {
  home: HomePage,
  about: AboutPage
};

const Page = (props) => {
  const Handler = PAGES[props.page] || ContactPage;

  return <Handler {...props} />;
};
```

### StrictMode Tag
 هیچ المان `DOM` اضافه‌ای رو رندر نمی‌کنه، بلکه `warning` ‌ها و `additional checks` رو برای فرزندان اون کامپوننت فعال‌می‌کنه. این کار فقط در حالت `development` فعال میشه.
```
function ExampleApplication() {
  return (
    <div>
      <Header />
      <React.StrictMode>
        <div>
          <ComponentOne />
          <ComponentTwo />
        </div>
      </React.StrictMode>
      <Footer />
    </div>
  );
}
```

### constructor VS getInitialState 
وقتی داریم از کلاس‌های `ES6` استفاده می‌کنیم باید `state‌` رو توی `constructor` مقداردهی اولیه کنیم و وقتی از `React.createClass` استفاده می‌کنیم باید از متد `getInitialState` استفاده کنیم.



###   super() VS super(props)
بیرون `constractor` فرقی نمیکند ولی اگر بخوان داخل کانستراکتور `props` را داشته باشه از `super(props)` باید استفاده کنیم



### Loop in JSX
only Array.prototype.map OR for statement




###  setState Vs replaceState
هر دو روی کلاس کامپوننت ها هستند setState مقادیر فعلی و قبلی با هم ترکیب میکنه. replaceState حالت فعلی رو با stateای که می‌خواییم جایگزینش می‌کنه 




### State change Detection
```
// class component
componentWillUpdate(object nextProps, object nextState)
componentDidUpdate(object prevProps, object prevState)

// function component
const [someState, setSomeState] = useState();
useEffect(() => {
  // code
}, [someState]);
```



### component without HTML rendering
```
render() {
  return false
}

render() {
  return null
}

render() {
  return []
}

render() {
  return <React.Fragment></React.Fragment>
}

render() {
  return <></>
}
```
توجه با مقدار undifined نمیشه کار کرد










# React Style (CSS)
```
const divStyle = {
  color: "blue",
  backgroundImage: "url(" + imgUrl + ")",
};

function HelloWorldComponent() {
  return <div style={divStyle}>Hello World!</div>;
}

<div
  style={{
    transform: "rotate(90deg)",
    WebkitTransform: "rotate(90deg)", // note the capital 'W' here
    msTransform: "rotate(90deg)", // 'ms' is the only lowercase vendor prefix
  }}
/>
```






# NOTES
- اگر `state` را مستقیم آپدیت کنیم کامپوننت ما ری رندر نمی شود.
  
- متدهای `Callback` در ریاکت معمولا به عنوان پارمترهای دوم هوکس ها می آیند و بعد از عملیات هوکس می شود کاری انجام داد.
```
setState({ name: "John" }, () =>
  console.log("The name has updated and component re-rendered")
)
```

- ویژگی `dangerouslySetInnerHTML` جایگزین ری‌اکت واسه استفاده از `innerHTML` توی `DOM` مرورگره و کارکردش درست مثل `innerHTML` هستش، استفاده از این ویژگی به خاطر حملات `cross-site-scripting(XSS)` ریسک بالایی داره.
  

- محیط `CLI` در ریاکت را اصطلاحا `CRA` میگویند که مخفف `create-react-app`

- اگر در تمپلیت از روش  Template strings استفاده کنیم باید کلمه کلیدی this را بزاریم اگر عادی استفاده کنیم نیازی نیست
```
<img className="image" src={"images/" + props.image} />

<img className="image" src={`images/${this.props.image}`} />
```

- برای اجرای برنامه بصورت SSL از دستور زیر استفاده می کنیم
```
"scripts": {
  "start": "set HTTPS=true && react-scripts start"
}
```

## React Routing
```
function App() {
  return (
    <Router>
      <Switch>
        <Route path="/" exact component={HomePage} />
        <Route path="/user/:userId" component={User} />
      </Switch>
    </Router>
  );
}

```
```
function HomePage() {
  const history = useHistory();
  const handleClick = () => {
    history.push('/about');
  };
  return (
    <div>
      <h1>صفحه اصلی</h1>
      <button onClick={handleClick}>انتقال به صفحه About</button>
    </div>
  );
}
```
```
function HomePage() {
  const history = useHistory();
  const handleClick = (userId) => {
    history.push(`/user/${userId}`);
  };
  return (
    <div>
      <button onClick={() => handleClick(123)}>انتقال به صفحه کاربر با شناسه 123</button>
    </div>
  );
}

function User({ match }) {
  const { userId } = match.params;
  return (
    <div>
      <h1>پروفایل کاربر با شناسه {userId}</h1>
    </div>
  );
}
```
