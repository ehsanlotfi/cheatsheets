### React Hooks
###### 1- useState
مدیریت استیت ها مثال شمارنده 
```
function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increase</button>
    </div>
  );
}
```
###### 2- useEffect
برای اجرای کد خاص در چرخه حیات کامپوننت، مثال فچ کردن داده ها هنگام بارگزاری کامپوننت
```
function FetchData() {
  const [data, setData] = useState([]);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/posts")
      .then((response) => response.json())
      .then((data) => setData(data));
  }, []); // اجرا فقط یکبار هنگام mount شدن

  return (
    <ul>
      {data.map((item) => (
        <li key={item.id}>{item.title}</li>
      ))}
    </ul>
  );
}
```
###### 3- useContext
برای استفاده از استیت های گلوبال مثال زیر پاس داده رنگ تم
```
import React, { useContext, createContext } from "react";

const ThemeContext = createContext("light");

function DisplayTheme() {
  const theme = useContext(ThemeContext);
  return <p>Current theme: {theme}</p>;
}
```
###### 4- useRef
دسترسی به عناصر دام مثال فوکوس روی تکس باکس
```
function FocusInput() {
  const inputRef = useRef(null);

  const focusInput = () => {
    inputRef.current.focus();
  };

  return (
    <div>
      <input ref={inputRef} type="text" />
      <button onClick={focusInput}>Focus</button>
    </div>
  );
}

```
###### 5- useReducer
شبیه useState است
برای مدیریت استیت ها در حالت پیچیده تر
توسط یک تابع ریدوسر میتونی مقدار استیت را عوض کنید
 ```
 const [state, dispatch] = useReducer(reducer, initialState)
 ```
 ```
 import React, { useReducer } from "react";

const initialState = { count: 0 };

function reducer(state, action) {
  switch (action.type) {
    case "increment":
      return { count: state.count + 1 };
    case "decrement":
      return { count: state.count - 1 };
    default:
      return state;
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <div>
      <p>Count: {state.count}</p>
      <button onClick={() => dispatch({ type: "increment" })}>+</button>
      <button onClick={() => dispatch({ type: "decrement" })}>-</button>
    </div>
  );
}
 ```
###### 6- useMemo 
یک مقدار را کش میکند
کش کردن دیتا و جلوگیری از محاسبه دوباره در ری رندر
مثلا در فیلتر کردن محصولات هزینه ری رندر کردن زیاد است فقط میتونیم بگیم زمانی رندر شود که گزینه فیلتر تغییر کند
```
const cachedValue = useMemo(calculateValue, dependencies)
```
کش کردن یک کامپوننت
```
  const memoChild = useMemo(() => <Child />, []);
```

###### 6- useCallback 
 یک تابع را کش میکند
 
### Virtual DOM
هر زمان داده های اصلی تغییر میکند دام مجازی با دام واقعی مقایسه می شود و تغییرات را اعمال میکند

### Props vs State
اولی ورودی های یک کامپوننت دومی متغیر های داخل یک کامپوننت

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
- تغییر رفتار رندر یک کامپوننت را میتوانیم مشروط کنیم بوسیله HOC که اصطلاحا بهش Render Hijacking میگویند.

##### What are the limitations of HOCs?
1. از HOC‌ها توی متد render استفاده نکنیم
2. متد‌های static باید کپی بشن وقتی HOC رو روی یه کامپوننت اعمال می کنیم، کامپوننت جدید هیچ کدوم از متد‌های استاتیک کامپوننت اصلی رو نداره
3. Ref‌ها رو نمیشه انتقال داد 

- همین مفهوم را در جاوااسکریپت هم داریم بهش میگیم `HOF ( Higher-Order Function )`
  که تابعی که یک تابع دیگه را به عنوان ورودی میگیره یا یک تابع را به عنوان خروجی return می کند

### Throttling vs Debouncing
فرض کنید مختصات اسکرول را میخوام بفرستیم وقتی بگیم بعد از 5 ثانیه که اسکرول نکرد بفرست میشه Debouncing ولی بگیم هر 5 ثانیه حداقل یکبار بفرست میشه  Throttling

### suspense component
وقتی بخواهی داده‌ها یا کامپوننت‌ها به صورت پویا (Lazy) بارگذاری شوند و در این مدت چیزی مثل یک متن "در حال بارگذاری..." نشان دهی.
```
const OtherComponent = React.lazy(() => import("./OtherComponent"));

function MyComponent() {
  return (
    <div>
      <Suspense fallback={<div>در حال بارگذاری...</div>}>
        <OtherComponent />
      </Suspense>
    </div>
  );
}
```

### Handlle component Re render
- PureComponent and shouldComponentUpdate in Class component
- React.memo in function Component
  
برای اینکه ری‌رندر شدن یه کامپوننت رو کنترل کنیم

### shallow comparison
وقتی که `props` یا `state` در کامپوننت تغییر‌می‌کنه، `PureComponent` یه مقایسه سطحی روی `props` و `state` انجام میده به این عمل `shallow comparison`  میگن.

### Synthetic events
رویدادهای مصنوعی یه رخداد `cross-browser` هست که به‌عنوان یه `wrapper` دور eventهای اصلی مرورگر قرار می‌گیره. رابط API برای کارکردن با اون دقیقا مثل رخداد native مرورگرهاست که شامل `stopPropagation` و `preventDefault` میشه، با این تفاوت که این رخداد‌ها بر روی همه مرورگرها کار می‌کنن.

### Ref and ForwardRef
در کلاس کامپوننت از `React.createRef` استفاده میکنیم و در فانکشن کامپوننت از هوکس `userRef` 
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
key تنها اتریبیوتی هستش که میشه به Fragment پاس داد
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
##### مزایای Strict mode
1. شناسایی کامپوننت‌ها با متد unsafe lifecycle.
2. هشدار در مورد استفاده از API مربوط به legacy string ref.
3. تشخیص side effect ها‌ی غیرمنتظره.
4. شناسایی API legacy context.
5. هشدار در مورد استفاده منسوخ findDOMNode.

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

### animation package
- React Transition Group
- React Spring
- React Motion

### React router
```
const Page = (props, context) => {

  // old version
  const history = useHistory();
  // new 
  const navigate = useNavigate();

  const navigate = useNavigate();
  const location = useLocation();
  const { slug } = useParams();

  return (
    <button
      type="button"
      onClick={() => {

        // old
        history.push("/new-location");

        // new 
        navigate("/new-location");

      }}
    >
      {"Click Me!"}
    </button>
  );
};
```

###  Shallow Renderer package
برای نوشتن یونیت تست کاربرد دارد و تا عمق یک یک کامپوننت را میتونیم بررسی کنیم.
```
function MyComponent() {
  return (
    <div>
      <span className={"heading"}>{"Title"}</span>
    </div>
  );
}
```
```
const renderer = new ShallowRenderer();
renderer.render(<MyComponent />);

const result = renderer.getRenderOutput();

expect(result.type).toBe("div");
expect(result.props.children).toEqual([
  <span className={"heading"}>{"Title"}</span>
]);
```

###  test Renderer package
می‌تونیم ازش برای رندر کردن کامپوننت‌ها و تبدیل اونا به یه  pure JavaScript استفاده کنیم
 این پکیج برای گرفتن snapshot از سلسله مرتب view(یه چیزی شبیه به درخت DOM) که توسط ReactDOM یا React Native درست میشه رو بدون نیاز به مرورگر یا jsdom فراهم می‌کنه.

### Flux Architecture
یک معماری که توسط فیسبوک مطرح شده است  شامل چندین قسمت اصلی است:
1. Action
2. Dispather
3. Store
4. View

### Redux ( state managment )
#### Three Principles
1. Single source of truth
2. State is read-only (only change by dispacher)
3. Changes are made with pure functions
#### Keyword
1. store
یک شی است که تمام وضعیت ها درون آن قرار دارد
2. Action مشخص میکند که چه تغییری در وضعیت برنامه باید رخ بدهد
3. Reducer استیت قبلی و اکشن فعلی را میگیرد و استیت جدید را می دهد
4. Containers کامپوننت هایی که تمپلیت ندارند
5. Components کامپوننت هایی که تمپلیت دارند
6. Selector برای انتخاب بخشی از استیت

#### مهمترین middleware های redux
- Redux Thunk
- Redux Promise
- Redux Saga.

#### redux-form
اطلاعات فرم‌ها رو توی state ریداکس مدیریت کنیم. ReduxForm می‌تونه با inputهای خام HTML5 هم کار کنه، ولی با فریم‌ورک‌های معروف UI مثل Material، ReactWidgets و ReactBootstrap کار کنه.

#### redux-thunk
 اجازه میده بتونیم action‌های async داشته باشیم.
بهمون این اجازه رو میده که actionهایی رو بسازیم که به‌جای action عادی تابع‌ برگردونن

#### redux saga
یک middleware برای مدیریت منطق جانب سرویس بصورت نخ های جداگانه (side effects) در اپلیکیشن‌های ریداکس است. 

##### put and call in react sega
هر دوی افکت‌های call و put سازنده‌های افکت هستن. تابع call برای ایجاد توضیح افکت استفاده میشه که به میان‌افزار دستور میده منتظر call بمونه. تابع put یه افکت ایجاد می‌کنه، که به store میگه یه action خاص رو فقط اجرا کنه.

### FLux ( state managment )
1. State can be changed
2. use multiple Store

### code-splitting
ویژگی پشتیبانی شده توسط باندلر‌هایی مثل webpack و browserify هستش که می‌تونه بسته‌های مختلفی ایجاد کنه که می‌تونه به صورت پویا در زمان اجرا بارگیری بشه.

### Imperative vs Declarative
- Imperative (دستوری): تمرکز روی چگونه انجام دادن (جزئیات).
- Declarative (بیانی): تمرکز روی چه چیزی انجام دادن (نتیجه).

یک دکمه لایک را در نظر بگیرید برای هندل کردن حالت های فعال و غیر فعال این دکمه دو تا راه حل وجود داره 
1. استفاده از یک کامپوننت و هندل کردن رنگ با if
2. استفاده از دو تا کامپوننت و هر رنگ جداگانه کامپوننت داشته باشد

# Hooks
- هوک‌ها رو فقط در ابتدای کامپوننت‌ها صدا کنیم. یعنی نباید هوک‌ها رو توی حلقه‌ها، داخل یا بعد ازشرط‌ها یا توابع تودرتو استفاده کنیم. با این کار اطمینان حاصل میشه که هوک‌ها با هر بار رندر کامپوننت به همون ترتیب صدا زده میشن و state‌ هوک‌ها بین رندرهای مختلف از useState ،useEffect حفظ میشه.
- هوک‌ها رو فقط داخل کامپوننت ری‌اکت می‌تونیم استفاده کنیم. توی توابع جاواسکریپت و خارج از درخت کامپوننت‌ها نباید هوک‌ها رو صدا بزنیم.
- بوسیله کتابخانه  eslint-plugin-react-hooks میتوانیم اطمینان حاصل کنیم از این شرط در پروژه ما اجرا شده.

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
- بستر React Router یه wrapper روی کتابخونه history هست که اعمال اجرایی بر روی window.history رو با استفاده از ابجکت‌های hash و browser مدیریت می‌کنه.

- برای چند زبانگی در React از کتابخانه React-Intl استفاده میکنیم.
- 
 ### basic rules in JSX
 - اگر بخواهیم تگ css استفاده کنیم به جای class از className استفاده می کنیم. چون class کلمه رزرو شده در js می باشد.
 - یک المنت ریشه واحد باید داشته باشیم.. تمامی کدها باید داخل یک المنت مثلا در react المنت App باشد.
 
 - کامنت را نمی توانیم مشابه html قرار دهیم بلکه باید مشابه js کامنت بگذاریم.

```
{/*comment*/}
```
 - هر المنت که باز می کنیم باید حتما ببندیم. مثلا اگر تگ br بخواهیم استفاده کنیم باید بگیم 
 ```
<br/>
```
- فقط به اندازه یک expression می توانیم داخل jsx از javascript استفاده کنیم. مثلا از حلقه استفاده کنیم .. مقدار یک متغیر را نمایش بدهیم...
 
 ```
const user= "Ehsan";

<div className="App">
  {user? <h1>Hello , {user}</h1> : <h1>Hello , User</h1>}
</div>
```

```
const Users = [
  {fistName:"Monica"},
  {fistName:"Ross"},
  {fistName:"Rachel"}
]

/* in JSX */
<div className="App">
 {Users.map(name =>(
  <h1>{name.firstName}</h1>
 ))}
</div>
```
### key 
یک ویژگی رشته ای است که در لیست ها مورد استفاده قرار میگیرد. این ویژگی کمک میکند ریاکت تغییرات را تشخیص دهد و هویت و ترتیب یونیک به هر آیتم می دهد
```
const ids = [1,2,3,4,5];
const listElements = ids.map((id)=>{
    return(
        <li key={id.toString()}>{id}</li>
    )
})
```
## React Components
در نسخه های قدیمی تر React این نوع کامپوننت ها statefull بودند و دارای چرخه حیاط و probs  بودند اما تابعی ها نبودند. برای همین برای حالت های state دار از کامپوننت های کلاسی استفاده می شد و برای نمایش از کامپوننت ها ی تابعی استفاده می شد. اما الان در نسخه های جدید کامپوننت های تابعی هم دارای چرخه حیاط هستند. معمولا برای کامپوننت های والد از کامپوننت های کلاسی و برای کامپوننت های فرزند از تابعی ها استفاده می کنیم.

ارسال آرگومان یا probs از کامپوننت والد به فرزند می باشد چون جریان داده از بالا به پایین هست . ما ارسال داده از فرزند به والد نداریم.

### class component
ارسال داده از کامپوننت والد به فرزند:
```
import {Component} from 'react';
import Apple from "./components/Apple";
import './Fruit.css';

class Fruit extends Component {

  render(){

    return (
      <div className="Fruit">
        <h1>نام کامپوننت فرزند</h1>
        <br/>
        <Apple number={10} colors={['yellow','red']} />
      </div>
    )
  }
}
```

دریافت داده در کامپوننت فرزند کلاسی
```
import {Component} from 'react';

class Apple extends Component {

  render(){
    const {colors} = this.probs;
    return (
      <div >
      <p> تعداد سیب ها :{this.probs.number}</p>
      </div>
    )
  }
}
```
### function component

دریافت داده در کامپوننت فرزند تابعی :

```
const Apple=(probs) => {
  console.log(probs);

  return (
    <div>
     <p> تعداد سیب ها :{probs.number}</p>
    </div>
  )
}

```

```
const Apple=({number}) => {
  console.log(number);

  return (
    <div>
     <p> تعداد سیب ها :{number}</p>
    </div>
  )
}

```

## Probs
 مقدار probs ها تغییر ناپذیر هستند و نباید در کامپوننت فرزند به طور مستقیم تغییر کنند. بلکه مقدار آن ها باید از طریق state تغییر کند.

 ما می توانیم انواع داده از جمله number , string,array,boolean را به کامپوننت فرزند بفرستیم.
 حتی می توانینم مدریت کننده های رویداد یعنی توابع را هم به صورت آرگومان از والد به فرزند بفرستیم تا در فرزند اجرا شوند.

### Probs children

 اگر کامپوننت فرزند را به صورت تگ باز وبسته جداگانه فراخوانی کنیم و داخل آن یک متن یا هر چیزی قرار دهیم به عنوان chilren

 ```
class Fruit extends Component {

  render(){

    return (
      <div className="Fruit">
        <h1>نام کامپوننت فرزند</h1>
        <br/>
        <Apple number={10} colors={['yellow','red']}/>
        <Apple>
          من سیب هستم
        </Apple>
      </div>
    )
  }
}
```
برای نمایش مقدار children در کامپوننت فرزند می توانیم به راحتی بنویسیم probs.children

### Probs validation
- install prop-types 

- use prop-types :

 ```
import PropTypes from 'prop-types';

const Counter = ({inc,dec,count}) => {
  return (

    <div>
      <h1>{count}</h1>

      <button onClick={inc}>+</button>
      <button onClick={dec}>-</button>

    </div>
  )
}

Counter.propTypes={
  inc:PropTypes.func,
  desc:PropTypes.func,
  count:PropTypes.number
}

export default counter
 ```
## State in React
وقتی از state استفاده می کنیم که بخواهیم داده ای را نمایش بدهیم .. تغییر بدهیم و ویرایش کنیم. State را نمی توانیم به صورت مستقیم تغییر بدهیم. بلکه باید از توابع خاصی استفاده کنیم.
### State in class Component 
نحوه تعریف State در کامپوننت کلاسی :

```
class App extends Component{
  constructor(){
    super();

    this.state={
      count:0,
      name:"Ehsan"
    }

  }

  render(){
    return(
      <div>
        <header>
          <h1>شمارنده من:</h1>
        </header>
      </div>
    )
  }
}
```

حالت رایج تر و بهتر تعریف State :

```
class App extends Component{
 
    state={
      count:0,
      name:"Ehsan"
    }

  render(){

    const {count,name}=this.state;
    return(
      <div>
        <header>
          <h1>شمارنده من:</h1>
        </header>
        <p>{count}</p>
         <p>{name}</p>
      </div>
    )
  }
}
```

تغییر State در کامپوننت کلاسی :

```
class App extends Component{
 
    state={
      count:0,
      name:"Ehsan"
    }

  changeState(){
    this.setState({count:5});
  }
  render(){

    let {count,name}=this.state;
    this.changeState();
    return(
      <div>
        <header>
          <h1>شمارنده من:</h1>
        </header>
        <p>{count}</p>
         <p>{name}</p>
      </div>
    )
  }
}
```
در این حالت برنامه اجرا می شود اما در کنسول خطا پشت سر هم چاپ می شود...علت خطا مربوط به چرخه حیاط هست..render می شود می بیند state تغییر کرده ..دوباره render می شود و یه حلقه مدام تکرار می شود.

### State in function Component

بزرگ ترین تفاوت تعریف state در کامپوننت کلاسی و تابعی این هست که وقتی یک state مثلا count را می خواهیم تغییر بدهیم لزومی به تغییر  بقیه state ها نیست..

برای کامپوننت های تابعی بعد از این که hook ها آمدند امکان تعریف State به وجود آمد:

برای تغییر state از یک hook به نام useState  استفاده می کنیم . خروجی دو شی هست یکی state و دیگری تابع تعریف state.  
در کامپوننت های تابعی متغیرهای state را جداگانه تعریف می کنیم و مثل حالت کلاسی همه را داخل شی state نمی گذاریم:

```
import {useState} from 'react';

const App = () => {

  const {count,setCount}=useState(0);
  const changeCount = () =>{
    setCount(5);
  }

}

```

## handling events with state

- events should be written in camel case
- with JSX you pass a function as the event handler , eather than a string :

in HTML : 
```
<button onclick="activateLasers()">
Activate Lasers
</button>
```
in react :
```
<button onClick={activateLasers}>
Activate Lasers
</button>
```
- ما می توانیم توابع مدیریت رویداد را در کامپوننت والد تعریف کنیم و به صورت probs به کامپوننت فرزند ارسال کنیم.
### 1- event handling in function component :

```
import {useState} from 'react';

const App = () => {

  const {count,setCount}=useState(0);
  const changeCount = () =>{
    setCount(5);
  }
  
  return (

     <div>
        <header>
          <h1>شمارنده من:</h1>
        </header>
        <p>{count}</p>
        <button onClick={changeCount}> تغییر شماره</button>
      </div>
  )

}

```
### 2- event handling in class component

تابع معمولی در کلاس به طور پیش فرض به this اشاره نمی کند . برای این که به this   اشاره کند. 
باید bind کنیم
```
class App extends Component{
 
  construcor(){
    super();

    this.state={
      count:0,
      name:"Ehsan"
    }
    this.changeName = this.changeName.bind(this);
  }
    
  changeName(){
    this.setState({name:"َAlireza"});
  }
  render(){

    return(
      <div>
        <header>
          <h1{this.state.name}</h1>
        </header>
       <button onClick={this.changeName}>تغییر نام</button>
      </div>
    )
  }
}
```

اگر changState را به صورت arrow function بنویسیم خودش میشه تابع کلاسی و نیازی به bind کردن در constructor نیست. 
```
changeName = () => {
 this.setState({name:"َAlireza"});
}

```
## چرخه حیات

### چرخه حیات در کامپوننت های کلاسی
- Mounting

1- constructor():

2- static getDerivedStateFrom():

وقتی که بسته به تغییر probلازمه که state هم تغییر بدهیم

3- render()

نمی توانیم قبل render داده نمایش بدهیم.
اگر در این متد از کامپوننت های دیگر استفاده کرده باشیم.. نحوه اجرا بدین صورت است که  بعد از اجرای render والد چرخه حیات  ساخت کامپوننت فرزند به طول کامل اجرا می شود و بعد از فراخوانی componentDidMount در فرزند متد متناظر در والد اجرا می شود.

4-componentDidMount

اینجا مطمءن هستیم که کامپوننت render شده است .. حالا می توانیم از سرور داده درخواست بدهیم و نمایش بدهیم.. می توانیم تا وقتی که داده نمایش داده شود یک spinner نمایش بدهیم.

- Updating

1- static getDerivedStateFrom(props,state):

2- shouldComponentUpdate(nextProp,nextState);

این جا می توانیم بعضی شرط ها را پیاده سازی کنیم که مثلا اگر فلان شرط برقرار بود بروزرسانی انجام بده در غیر این صورت انجام نده... اگر false برگرداند چرخه حیات بروزرسانی متوقف می شود.

3- render()

4- getSnapshotBeforeUpdate(prevProp,prevState)

یک backup قبل از بروزرسانی انجام می دهیم مثلا وقتی کاربر داره اسکرول می کنه قبل از این که روی یک پست یا button کلیک کنه می خواهیم محل positon کاربر را داشته باشیم مثلا تا کجا اسکرول کرده

5- compoenentDidUpdate(prevProp,prevState,snapshot)

این جا snapshot در دسترس هست..

- Unmounting

1- componentWillUnmount

وقتی کاربر تب مرورگر را می بندد  این چرخه حیات فراخوانی می شود.. یا مثلا از کامپوننت بیرون می آید..در این متد مثلا می توانیم connection را close کنیم..

### چرخه حیات در کامپوننت های تابعی

چرخه حیات در کامپوننت های تابعی توسط هوک useEffect انجام می گیرد

1- mount : 

```
useEffect(() => {

  console.log('for mounting we just use []');

},[]);
```
2- update

```
useEffect(() => {

  console.log('for updating we should put our state we want to update in []');

},[color]);
```

3- unmount

we should return annonymouse function
```
useEffect(() => {

  console.log('for mounting we just use []');

  return() => {
    console.log('for unmounting ..');
  }

},[]);
```

## Context

بعضی وقت ها پیش می آید که لازم هست یک state یا event handler یا به طور کل ی داده را از کامپوننت A به Bو از B به C بفرستیم بدون این که در B استفاده ای بکنیم .

با context داده را می توانیم در والد تعریف کنیم و همه کامپوننت های زیرمجموعه به آن دسترسی داشته باشند بدون این که به طور مستقیم داده را بین کامپوننت ها پاس بدهیم.

عیب: استفاده زیاد از contextباعث می شود که استفاده مجدد از کامپوننت سخت شود. 
وقتی از context زیاد استفاده می کنیم جلوی render مجدد را نمی توانیم بگیریم.

### API
ما می توانیم یک فایل جداگانه داشته باشیم مثلا MyContext.js و درون آن  به صورت زیر مقادیر MyContext را تعریف کنیم:
```
const Mycontext = React.createContext(defaultValue);
// or

const Mycontext = React.createContext({
  loading:false,
  setLoading:() => {},
  contact:{},
  setContact:() => {},
  .....
});
```

در والد باید context را برای فرزندان تامین کنیم:
باید در کد jsx تگ های فرزند را درون تگ Myconext.Provider  قرار دهیم
```
<MyContext.Provider value= {{
  loading,setLoading,contact,deleteContact:confirmDelete,
}
}>
  <div class="App">
    <Navbar />
    <Routes>
    .
    .
    .
    </Routes>

  </div>
</MyContext.Provider >
```

نحوه استفاده از Context در کامپوننت های تابعی:

```
const value= useContext(Mycontext);
```
مثلا در کامپوننت Nabar به جای این که probs را از App  به آن بفرستیم از useContext استفاده می کنیم:

```
const {contactQuery,contactSearch}= useContext(ContactContext);
```

استفاده در کامپوننت های کلاسی (در داخل کلاس)
```
class MyClass extends React.Component {

  static contextType = MyContext;
  render(){
    let value=this.context;
  }
}
```

خارج کلاس :

```
class MyClass extends React.Component {

}
MyClass.contextType=MyContext;
  
```

مصرف context در زیرمجموعه ها :

در این حالت فقط در کد jsx قابل استفاده است.
```
<MyContext.Consumer>
{value=> /* ... */}
</MyContext.Consumer>
```

## React Hooks

### useState 
- معادل setState در کامپوننت های کلاس محور می باشد.
- برای ایجاد و ویرایش state ها در React مورد استفاده قرار میگرد.
```
const [count, setCounter] = useState(0);
const setCount = () => {
  setCounter(count + 1);
÷2};
```

### useEffect
 هر بار که یک state تغییر کند، یک افکت ایجاد می‌کند.در چرخه حیات کامپوننت های تابعی توضیح دادم
 
 - use  useEffect

ما می توانیم از چرخه حیات mount, unmount هم استفاده کنیم
### useContext

در مبحث context توضیح داده شد
 ### useRef
برای فراخوانی یک عنصر در DOM استفاده می شود.
در کد زیر refContaier یک object هست که فقط property به نام current دارد . که با initailValue مقداردهی می شود.
```
const refContainer = useRef(initialValue);
```

```
const inputRef = useRef(null);
const focusInput = () =>{
  inputRef.current.focus();
}

return (<>

<input ref={inpurTef} type="text" className="form-control" placeholder="something.." />
</>
<button type="button" onClick={focurInput}>
</button>
)
```
حتی با این هوک می توانیم سایر ویژگی های   یک عنصر Dom مثلا در این جا className,plaeholer و غیره را تغییر بدهیم.
کاربرد دیگر می توان برای نگه داشتن مقدار قبلی state از آن استفاده کرد.

برای شمردن تعداد render ها اگر از state استفاده کنیم چون تفغییرش باعث render مجدد میشه  در حلقه گیر می کند اما با useRef می توان استفاده کرد

```

const renderCount= useRef(1);

useEffect ( () => {
  renderCount.current=renderCount+1;
}

)
```

کاربردهای دیگر:
 مدیریت فوکس - انتخاب متن و media playback
 فعال سازی انیمشین های ضروری
 استفاده برای کتابخانه های مجزا برایDom

نکته اخر: زیاد و پشت سر هم استفاده نکنید!
### useSearchParam

در کتابخانه react-router-dom هست.. به جای این که داده را درون state ذخیره کند درون url  نگه می دارد.

```
const [searchParams, setSearchParams] = useSearchParams();
```
نحوه استفاده در تگ input :

```
<input
type="text"
value={ searchParams.get("filter") || "" }
onChange= {(event) => {
  let filter=event.target.value;
  if(filter){
    setSearchParams(filter);
  }
  else{
    setSearchParams({});
  }
}}
placeholder="[جست و جو]"
/>
```

### useLocation
 خروجی این هوک یک شی هست که موارد مهمی را در بردارد از جمله pathname,search ,state

```
const location= useLocation();
```
 استفاده از search در location : وقتی ما محتوای search کاربر را  به url مان در تگ link در صفت to اضافه کنیم دیگر با کلیک روی لینک نتیچه جست وجو ی ما reset نمی شود:

```

<Link
to={`/books/${book.number}{location.search}`}$
 key={book.number} >
 {book.name}
</Link>
```
### useNavigate

 وقتی استفاده می کنیم که 
کاربر را بخواهیم به صفحه خاصی redirect کنیم .. مثلا بدون این که link ایجاد کنیم.

### useMemo 
عملکرد این هوک هم شبیه به useCallBack هست با این تفاوت که به جای یک تابع یک مقدار memoized شده رو برمیگردونیم .

```
const memoizedValue= useMemo(()=> computeExpensiveValue(a,b), [a,b])
```

```
const [colorChange,setColorChange] = useState(false);
cost [number,setNumber]=useState(0);
const doubleNumber= useMemo(( = > superSlowFunction(number),[number]));

//refrential equality
const appStyle = useMemo (() = >{
  return {
    backgroundColor= colorChange ? 'red' : 'white';
  }
}),[colorChange];

useEffect(() =>{
  conslo.log('backgroundColor changed');
},[appStyle])
```

استفاده از این هوک کمک می کنه که وقتی بنا به دلیلی render مجدد انجام شد مثلا state تغییر کرد یا هر چیزی در صورتی تابع compueteExpnesivevalue اجرا بشه که یکی از ورودی ها حتما تغییر کرده باشه .. برای حل مشکل refrential equlity

### useCallBack 
یک تابع رو میگیره و اون رو کَش میکنه یا به نوعی تو مموری ذخیرش میکنه و به ما تحویل میده.
  شبیه useMemo هست .. برای حل مشکل refrential equlity استفاده میشه .. در مثال مشابه useMemo مثلا برای این که وقتی یک دکمه را زدیم که state مربوط به colorChange تغییر کنه می بینیم که getItems هم چون به object نسبت داده شده دوباره اجرا می شود... ما با useCallback انرا wrap می کنیم تا هر وقت number تغییر کرد فقط دوباره اجرا بشه

  ```

//refrential equality
const appStyle = useMemo (() = >{
  return {
    backgroundColor= colorChange ? 'red' : 'white';
  }
}),[colorChange];

const getItems= useCallBack( () = > {
  return [number,number+1 , number +2];
},[number])
;s
useEffect(() =>{
  conslo.log('backgroundColor changed');
},[appStyle])
```
### useReducer

این هوک یک جایگزین برای useState هست.. در واقع برای مدیریت state استفاده می شه.. در واقع این هوک redux را پیاده سازی میک نه..
```
const [state,dispatch]= useReducer(reducer,initialArg,init);
```
فرض کنید که ما یکstate به نام count داریم و دو دکمه داریم یکی برای کاهش و دیگری افزایش.. با دکمه کاهش ما توسطsetCount مقدار state را به راحتی کاهش می دهیم و توسط دکه افزایش افزایش می دهیم

حالا می خواهیم از این هوک استفاده کنیم

```
const reducer=(state,action) =>{
  switch(action){
    case 'INC':
    return {
      count:state.count+1
    };
    case 'DEC':
    return{
      count:state.count -1
    };
    default:
    return state;
  }
}

const ourComponent = () = >{

  const [state,dispatch]= useReducer(reducer,{count:0});

  const increment= () => {
    dispatch({type:"INC"});
  }

  const decrement= () => {
    dispatch({type:"DEC"});
  }

}
```

حالا در کد jsx : 

```
<button onClick={increment}>
</button>
<button onClick={decrement}>
</button>

```

### useLayoutEffect 
این هوک شبیه به useEffect هست ولی useLayoutEffect قبل از این که صفحه render بشه و به کاربر نمایش داده می شود. به صورت synchronuus اجرا می شود. درحالیکه useEffect به صورت async اجرا می شود.

steps before useEffect funtion runs
1- User take action -> clicking some button
2- React changes the state
3- React handles DOM mutation
useLayoutEffect runs
4-Browser prints Dom changes to browserscreen
5- After browser prints Dom changes to screen then useEffect runs

اگر ما هم useEffect داشته باشیم و هم useLayoutEffect   اول useLayoutEffect اجرا می شود بعد useEffect
### useImperativeHandle 

برای ویرایش یک Ref در کامپوننت پدر استفاده می شود.  در واقع برای شخصی سازی ref در کامپوننت پدر در فرزند استفاده می شود.

علت استفاده این هست که کد زیر خطا تولید می کند و کار نمی کند :

```
import {useRef} from "react";

let BootstrapInput = (props) => {
    return <inpput  {... props} />;
};

const UseImperativeHandleExample = () => {

    const inputRef= useRef(null);

    const handleFocus = () => {
        inputRef.current.focus();
    };

    return(

        <div className="w-50 d-grid gap-3 mx-auto mt-5">
            <h5 className="alert alert-success text-center">
                آشنایی با هوک  useImperativeHandle
            </h5>
           <hr className="bg-danger"/>
            <input 
                ref={inputRef}
                type="text"
                className="form-control"
               
            />
            <BootstrapInput  type="text" className="form-control" ref={inputRef} /> 
            <button type="button" className="btn btn-success btn-block " onClick={handleFocus}>
            تمرکز بنما
            </button>
        </div>
    );
}

```

خطایی که در مرورگر می دهد  و می گوید که حتما باید از forwardRef , useImperativeHandle استفاده کرد:

```
 Warning: Function components cannot be given refs. Attempts to access this ref will fail. Did you mean to use React.forwardRef()?

Check the render method of `UseImperativeHandleExample.
```
استفاده تنهایی از forwardRef مشکل را حل نمی کند .بلکه باید ref ر ا به صوت آرگومان مجزا از props به CostomizedInput بدهیم . 

کامپوننت فرزند:
```
let CostomizedInput = (probs,ref) => {
  // has it`s own ref`
  cost ref2= useRef();
  useImperativeHandle(ref,() = > ({
    focus: () => {
      ref2.current.focus;
      alert('Hello');
    }
  }));
  return <input ref={ref2} {...probs}/>;
}

// use forwardRef 
CostomizedInput=forwardRef(CostomizedInput);

```
از forwardRef له این علت استفاده می شه که ما نمی تونیم ref را شبیه سایر pobs  ها پاس بدهیم

در کامپوننت پدر:

```

const inputRef = useRef(null);
const handleInput=()=>{
  inputRef.current.focus();
}

// in return jsx

return (
  <div>
    <CostomizedInput  type="text" className="form-control" ref={inputRef} />
    <button className="btn" onClick={handleInput}> click me! </button>
  </div>
)
```
### useDeferredValue 
این هوک یک مقدار رو میگیره و یه کپی از اون برمیگردونه که برای اپدیت های ضروری تر به تعویق می ندازه..مثلا اگر render حاضر نتیجه یک اپدیت ضروری باشد مانند input کاربر، React مقدار قبلی را برمی گرداند و بعد مقدار جدید را بعد از این که render ضرری کامل شد render می کند.
برای حل مشکل عدم رسپانسیو بودن در نسخه های جدید تر آمده است.

این هوک تنها مقداری که به آن پاس داده می شود به تعویق می اندازد. اگر می خواهید جلوگیری کنید از یک کامپوننت فرزند برای render مجددد براثر اپدیت ضروری، باید از useMemo  هم استفاده کنیم

مثال: کاربر در input  عبارتی را جست  وجو می کند و هم زمان این عبارت جست و چو در حال سرچ در پایگاه داده هست پردازش کمی طولانی است این پردازش در useMemo  باید نوشته شود.  اگر از DeferedValue استفاده نشود مثلا کاربر عدد 1 وارد می کند اول باید عدد 1 پردازشش تمام بشه تا کاربر بتواند عدد را وارد کند مثلا کاربر چند تا عدد پشت سر هم می زند ولی حتی در inputنوشته نمی شود  بلکه همزمان با نتیجه پردازش نمایش داده می شود. راه حل استفاده از deferedValue هست تا حداقل کاربر هر چیزی وارد کرد در input بافاصله نمایش داده شود. بعد نتایج نمایش داده شود.

```
const ChildComp = ({value}) => {
  const deferedValue= useDeferedValue(value);
  const slowProcess= useMemo(()=> {
    //some processing
  },[deferedValue]);

  useEffect( () => {
    console.log(`value : ${value}`); // value=123
    console.log(`deferedValue : ${deferedValue`);// deferedValue=12
  })
}

const UseDeferedValueExample = () => {
  const [value,setValue] = useState(0);

  return (
    <input type="number" value={value} onChange={e => setValue(e.target.value)}
    
    <ChildComp  value={value} />
    />
  )
}
```

### useTransition 
این هوک هم مانند useDereferdValue برای حل مشکل عدم رسپانسیو بودن در نسخه های بالاتر طراحی شده است. این هوک بهتر از useTransition هست..
مانند هوک useDefredValue لازم نیست از هوک دیگری استفاده شود.
مثال مانند مثال بالا هست: کاربر در input عدد وارد می کند و در پایین لیست بزرگی چاپ می شود وقتی پشت سر هم عدد وارد کنیم هنگ می کند. غیر رسپانسیو می شود. ما می خواهیم عملیات محاسبه و چاپ لیست به تعویق بیفند . در واقع می خواهیم کار نمایش input کاربر در input اولویت بیشتری نسبت به چاپ لیست که عملیات سنگینی هست داشته باشد. وقتی کار اولی تمام شد کار دومی شروع شود.

```

const UseTransitionExample = () => {
  const [isPending,startTransition] = useTransition();
  const [value,setValue] = useState(0);
  const [list,setList] = useState([]);

  const handleChange = (e) =>{
    setValue(e.target.value);

// less priority for heavy processing
    startTransition = (() => {
      const numbersList= [];
      let count=0;
      while(count < =1000){
      numbersList.push(e.target.value);
   
      setList(numbersList);
      }

    });
  } ;

  return (
    <input type="number" value= {value} onChange={handleChange} />

    {isPending ? "در حال بارگذاری..." :
    list.map((item,index)=> {
      return <div key={index}>{`عدد برابر است با ${item}`} </div>
    })
    }
  );

}
```
بعد از استفاده از این هوک application هنگ نمی کند و کاربر که عدد پشت سرهم وارد می کند بلافاصله نمایش داده میشود.
### custom hoook
مانند نوشتن تابع هست ولی بهتر هست که با use شروع شود تا react آن را به عنوان هوک تشخیص دهد. مثلا ساخت یک هوک برای fetch کردن داده ها :

```
const useFetch = () => {

  const [data,setData]= useState(null);
  useEffect ( ()=> {
    fetch(url).then ((res) => res.json()).
    then ((data) => setData(Data));
  },[url]

  );
}

const CustomHooks = () =>{

  const [users] = useFetch("https://jsonplaceholder.ir/users");
}
```
بهتر است که هر هوک در فایل جداگانه ای باشد.
### useDebugValue 
برای دیباگ یک فانکشن استفاده میشود و زمانی اجرا میشه که React DevTools باز باشه .

می تواند برای نمایش یک label برای هوک های سافرشی در ReactDevTools  استفاده شود.
```
useDebugValue(value);

function userFriendStatus(friendID){
  const [isOnline,setIsonLine]= useState(null);

  // showa label in DevTools next to this hook
  useDebugValue(isOnline? 'isOnline': 'offline');
  return isOnline;
}
```

### useId 

برای تولید id های یونیک رشته ای استفاده می شود. اما هیچ وقت نباید برای تولید keys  در لیست استفاده شود. keys  باید از data تولید شود.
```
function CheckBox(){
  const id= useId();

  return (
    <>
      <label htmlFor
      
      ={id}> Do You like React ?</label>
      <input id={id} type="checkbox" name="react" />
    </>
  );
}
```

### (Library Hooks) useSyncExternalStore 
 
 برای وقتی استفاده میشه که قراره از یه منبع خارجی یک سری دیتا بخونیم
### (Library Hooks) useInsertionEffect 
عملکردی مثل useEffect داره با این تفاوت که قبل از این که DOM اجرا شده باشه عمل میکنه

### Rules of Hooks

هیچ وقت هوک ها را از توابع معمول جاوااسکریپت فراخوانی نکنید در عوض می توانید آن ها را  در کامپوننت های تابعی یا custom hook ها فراخوانی کنید
با رعایت این قانون می توانیم مطمین شویم که هر بار کامپوننت render می شود hook های ما فراخوانی می شوند.
هم چنین  هیچ وقت هوک ها را درون شرط ها ، حلقه ها و توابع تو در تو فراخونی نکیند.
## Services in React
1- initialize nodejs  in subfolder server in the directory of project

2- instal json-server

3- crate file db.json for our data

4- change package.json so when we "start" it uses db.json :

```
"scripts" {
  "start" : "json-server --watch db.json -p 9000"
}
```
5- use command "npm start" for executing data base

6- use axios for connecting to database

```
import axios from 'axios';

class DataService {
  static async fetchData() {
    try {
      const response = await axios.get('https://api.example.com/data');
      return response.data;
    } catch (error) {
      throw new Error('Error fetching data');
    }
  }
}
```
we should use in useEffect:
```
const App = () =>{

  const [loading,setLoading]=useState(false);
  const [contacts,setContacts]=useState([]);
  const [groups,]=useState([]);

  useEffect( () =>{
    const fetchData=async() => {
      try{
        setLoading(true);
        const {data : contactData}= await axios.get("http://localhost:9000/contacts");

        const {data : }= await axios.get("http://localhost:9000/groups");
        
        setContacts(contactData);
        setGroups(groupData);
        setLoading(false);

      }
      catch(err){
        console.log(err.message);
        setLoading(true);
      }

    };

  }, []);
}
```
البته راه حل بهتر این هست که سرویس ها را در فایل جداگانه مثلا services.js بنویسیم و بعد درون کامپوننت ها استفاده کنیم:

```
import axios from "axios";
const SERVER_URL = "http://localhost:9000";

export const getAllContacts = () => {
  const url = `${SERVER_URL}/contacts`;
  return axios.get(url);
}
```

## Loading show

// در کامپوننت یا فایل مورد نظر

```
import { useState, useEffect } from 'react';
import axios from 'axios';

function DataComponent() {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    const fetchData = async () => {
      try {
        const response = await axios.get('https://api.example.com/data');
        setData(response.data);
      } catch (error) {
        console.error('Error fetching data:', error);
      } finally {
        setLoading(false);
      }
    };

    fetchData();
  }, []);

  if (loading) return <p>Loading...</p>;

  return (
    <div>
      {/* show Data */}
      {data && (
        <ul>
          {data.map(item => (
            <li key={item.id}>{item.name}</li>
          ))}
        </ul>
      )}
    </div>
  );
}

```
## Style in React

### 1- Inline styling  

style attribute in JSX accepts JS object with camelCased properties
```
const diveStyle={
  color: 'blue',
  backgroundImage:'url('+imgUrl+')',
  height:10 , 
};

function HelloWorldComponent(){
  retrun <div style={diveStyle}>Hello World!</div>;
}
```

```

function HelloWorldComponent(){
  retrun <div style={{color:'aqua' , border:'1px solid red'}}>Hello World!</div>;
}
```
این مدل استایل دهی بیشتر برای استایل دهی داینامیک استفاده می شود. 

```

<h1 style={{color: count===0 ? 'red' : 'green'}}> 
{count}</h1>

/* or */

<h1 style={count===0 ? {color:'red'} : {color:'green'}}> 
{count}</h1>

```

### 2- write css in style.css (global style) 
ایجاد پوشه public  و سپس داخل آن پوشه css و بعد داخل آن فایل style.css ایجاد کنیم 
این فایل را مستقیما می توانیم در index.html لینک بدهیم.

فایل index.html هم درون پوشه public قرار دارد.
```

<link rel="stylesheet" href="css/style.css">
```

### 3- use .css file for each component  (global style)
برای مثال App.css و یا index.css . برای استفاده باید در فایل index.js  و App.js به ترتیب فایل css متناظر import شود.

استایل های تعریف شده در این دو فایل در مرورگر کجا نمایش داده می شوند ..کجا می توانیم ببینیم؟.. 
فریم ورک React این ها را به صورت دو تگ style در ادامه تگ head می چسباند اگر در مرورگر به تب elements مراجعه کنیم قابل مشاهده هستند.

یعنی محتوای دو فایل داخل source خود html قرار می گیرد.

### 4- use css module

وقتی ما کد css درون فایل هایApp.css یا index.css یا حتی style.css می نویسیم scope اصلی global هست..
 
اگر ما بخواهیم برای هر کامپوننت به صورت global استایل ندهیم باید چیکار کنیم؟
می خواهیم به صورت local فقط برای همین کامپوننت باشد 

یا این که مثلا ما دو تا کامپوننت داریم هر کامپوننت یک فایل css دارد ..به هر دلیلی فرض کنید ما از یک نامی برای css class استفاده کردیم که در هر دو کامپوننت یکسان هست.. ما می خواهیم 
اگر یکی را اعمال کنیم برای هر دو اعمال می شود. چون scope به صورت global هست.
برای حل این مشکل از css module استفاده می کنیم :
یک scope محلی فقط مختیص کامپوننت ایجاد می شود.
برای هر کلاس css یک کد هش ایجاد می کند که مختص کامپوننت هست و به این صورت با دیگر کلاس های کامپوننت های دیگر متفاوت می شود.

برای کامپوننت App یک فایل App.module.css ایجاد می کنیم.  و موارد css های خود را داخل آن قرار می دهیم و سپس در کامپوننت خودمان import  می کنیم.

```
//import '.App.css';
import styles from '.App.module.css';
```
نحوه استفاده به این صورت هست :

```
<div className={styles.App}>
  <header className={styles.AppHeader}></header>
</div>
```
 در حالیکه برای حالت global نحوه استفاده به این شکل بود:
 ```
<div className="َApp">
   <header className="App-header"></header>
</div>
```

کد css در App.moduel.css و App.css :
```

.App{

  text-align:center, 
  ....
}
```

َ
نحوه تولید شدن کلاس css برای App :
ابتدا نام کامپننت و سپس نام کلاس css و سپس کد هش 

```
.App_App__B2Fbb{

  text-align:center, 
  ....
}
```

## React routing

### 1- install and import react-router-dom
### 2- use Browser Router in index.jsx as a Parent of App

```
import {BrowserRouter} from "react-router-dom";
root.render(
  <React.StrictMode>
    <BrowserRouter>
      <App />
    <BrowserRouter/>
  </React.StrictMode>
);

```
### 3- define routes
لینک ها در هر جا تعریف شده است Route ها باید در والد آن تعریف شود. مثلا اگر لینک ها در App تعریف شده Route ها باید در index.jsx تعریف شود:

```
import {BrowserRouter,Route,Routes} from "react-router-dom";

root.render(
  <React.StrictMode>
    <BrowserRouter>
      <Routes>
        <Route path="/"  element={<App/>}/>
        <Route path="/books"  element={<Book/>}/>
        <Route path="/books/:bookId"  element={<Book/>}/>
      </Routes>
    <BrowserRouter/>
  </React.StrictMode>
);

```

### 4- define links

```
<Link  to="/books">  کتاب ها </Link>
```

### link in a list of items

```
{books.map((book) => (
<Link to={`/books/${book.number}`}
key="{book.number}"
>
{book.name}
</Link>
))}

```

### get params from Url
برای Route زیر :

```
  <Route path="/books/:bookId"  element={<Book/>}/>
```

با استفاده از هوک useParams در کامپوننت Book پارامتر bookId را دریافت می کنیم:

```

import {useParams} from 'react-router-dom';

const books = () => {
  const params = useParams();

  return (
    <div>
      <p> کتاب با شناسه : {params.bookId}</p>
    </div>
  );
}
```
### outlet
 مثلا ما یک کامپوننت اصلی App داریم ویک کامپوننت Book داریم می خواهیم وقتی به کامپو.ننت Book می رویم یعنی مسیر /books  کامپوننت App هم چنان مثلا در Navbar باشد .. برای این کار باید Route مربوط به Book را داخل Router مربوط به App به صورت فرزند تعریف کنیم :

1- 
 ```

<Routes>
  <Route path="/"  element={<App/>}>
    <Route path="/books"  element={<Book/>}/>
    <Route path="/books/:bookId"  element={<Book/>}/>
  </Route>
  
</Routes>

```

2- استافده از تگ outlet در App 

```
const App = () => {

  return (

    <div className="App" >
    <p>کتابخانه </p>
    <Nav>
      <Link to ="/books"> کتاب ها
      </Link>
    </Nav>
    <outlet />
    </div>
  );
}
```

### define route Not Found

می خواهیم وقتی کاربر در مرورگر خود url را تایپ کرد که جزو مسیرهای ما نبود اتوماتیک یک کامپوننت not Found برای او نمایش داده شود:

```

// after all routes
<Route 
path="*" element = {
  <main styke = {{padding: "1 rem "}} >
    <p> یافت نشد</p>
  </main>
  
}
/>

```

## مباحث پیشرفته

### StrictMode
برای برحسته کردن مشکلات احتمالی در application استفاده می شود.  Strict Mode هیچ UI را renderنمی کند. بلکه چک های اضافی و هشدارهای را فعال می کند. StrictMode فقط برای فرزندانش کار می کند.

مواردی که StrictMode کمک می کند:

1- تشخیص کامپوننت ها با چرخه حیات ناامن
 2- هشدار دادن در مورد نحوه استفاده از رشته ref API    

 3- هشدار در مورد استفاده منسوخ شده findDomNode
 
 4- تشخیص اثرات جانبی غیرمنتظره
 5- تشخیص legacy ContextAPI
 6- مطمین شدن از قابلیت استفاده مجدد از State

 StrictMode  در نسخه های جدید تر 18 به بعد باعث می شود که useEffect دوبار mount شود. یعنی یک بار mount  سپس unmount و دوباره mount می کند.
 اگر StrictMode را حذف کنیم useEffect یک بار mount می شود. 

 مشکلی وجود ندارد از نظر سازندگان react چون هنگام build  شدن یک بارmount می شود. 

 ### Debounce
 مثلا search input سایت را در نظر بگیرید .. ما هر کاراکتری که وارد کنیم در eventHander می رود و اون کاراکتر را  در داده جست و جو می کند. برای داده های زیاد این باعث هنگ کردن سایت می شود. برای جلوگیری از این کار بعضی از سایت ها این طوری پیاده سازی می کنند که وقتی کاربر یک کاراکتر وارد کرد بهش مثلا 1 ثانیه دیگر وقت می دهند تا کاراکترهای دیگرش را وارد کند و همین طور مدام این زمان را reset  می کنند این طوری کاربر 
وقتی  تایپش تمام شد عملیات جست و جو آغاز می شود . به این کار deboune کردن می گویند.

روش های پیاده سازی : 

- use SetTimeout

```
let filteredTimeout;

const  search=(query) => {
  
  // built-in js funciton
  clearTimout(filteredTimeout);
  if(!query) return setFilteredData([... data]);

  filteredTimeout=setTimount( () => {
    setFilterdData(
      data.filter((item)=>{
        return item.name.toLowerCase().includes(query.toLowerCase());
      })
    )
  }
, 10000
  );
}
```

- use ready library in npmjs site :
  - react-debounce-inputs
  - lodash.debounce

### Throttle

برعکس debounce هست می خوایم مثلا یه کاری توی 1 ثانیه بیشتر از 1 بار اجرا نشود . فرض کنید که شما احراز هویت می خواهید انجام بدید و می خواهید توی 5 دقیقه فقط حداثر یک درخواست ارسال شود. مثلا دکمه ارسال رمز با پیامک توی  5 دقیقه یک بار ارسال شود.

برای پیاده سازی Throttle میشه از js خام استفاده کرد و با react پیچیده می شود.

میشه از کتابخانه های آماده استفاده کرد مانند lodash.thorttle :

```
import throttle from 'loadash.thorottle';
const App = () =>{

  const [count,setCount]= useState(0);

  const logCount=(count) = >{
    console.log(`INCREMENT ${count}`);
  }

  const throttleLog= useCallback(throttle(logCount,1000),[]);

  const increase=() => {
    setCount(count+1);
    throttleLog(count);
  }
}
```
### Lodash
یک کتابخانه js حاوی توابع بسیار زیاد هست که کارهای مهمی را انجام می دهند. مثلا می خواهید آرایه ای از اعداد را با هم جمع کنید و خروجی بگیرید یا توی آرایه ای از اسامی ، اسامی منحصر بفرد را استخراج کنید. یا بخواهید یک رنج از اعداد را تولید کنید  یا بخواهید یک clone از یک object پیچیده بگیرید.

## اعتبارسنجی فرم ها
برای اعتبارسنجی مقادیر input ها در فرم دو راه داریم :

1- خودمان شرط بنوسیم که مثلا حتما فیلدهای اجباری پر شده باشد برای فیلدهای عددی حتما عدد وارد شده باشد.

### YUP
2- استفاده از کتابخانه Yup

- ابتدا نصب با استفاده از npm
- یک پوشه validation ایجاد می کنیم و کدهای schema را اون جا قرار می دهیم 

- scheme :

```
// in src/validations/contactValidation.js :

import * as Yup from 'yup';

export const contactSchema = Yup.object().shape({

  fullname:Yup.string().required('نام و نام  خانوادگی الزامی می باشد'),
  photo:Yup.string().url('آدرس معتیر نیست').required('تصویر مخاطب الزامی می با شد'),
  mobile:Yup.number().required('شماره موبایل الزامی می باشد'),
  email:Yup.string().email('آدرس ایمیل معتبر نیست').required('آدرس ایمیل الزامی می باشد'),
  job:Yup.string().nullable(),
  group:Yup.string().required('انتخاب گروه الزامی می باشد'),
});
```
- use in App.js in createContactForm :

```
import { contactSchema } from './validations/contactSchema'; 

// add new state :
const [errors,setErrors] = useState([]);

  const createTaskFrom = async(event) => {
    event.preventDefault();
    try {
      setLoading((prevLoading) => !prevLoading);
     
     //added
      await contactSchema.validate(contact);
    //

      const {status,data} = await createContact(contact) ;
      console.log(status);
           
      if(status ===201){
        const allContacts= [... contacts,data];
        setContacts(allContacts);
        setFilteredContacts(allContacts);
        setContact({});
        setLoading((prevLoading) => !prevLoading);
        navigate("/contacts");
      }
    } catch (error) {
      console.log(error.message);
      console.log(error);
      setLoading((prevLoading) => !prevLoading);
    }

  }
```
the console will show only last eror :

ValidationError: انتخاب گروه الزامی هست

- the contactForm should not have any attribute required in form
- for showing all Errors in console :

```
 await contactSchema.validate(contact , {abortEarly : false});
```

output : 
4 errors occurred
App.js:141 ValidationError: 4 errors occurred

- if we want to show detail of error :
```
console.log(error.inner);
```

### formik
 با استفاده از formik دیگر نیازی به Yup نداریم چون خودش اعتبارسنجی را انجام می ددهد.

1- imports need in AddTask
 ```
import { useFormik } from "formik";
import { taskSchema } from "../../validations/taskValidation";
```

2- build schema and validation

```
 const formik = useFormik({
        initialValues : {
            Title:"",
            Category:"",
            Priority:"",
            Color:"",
            Description:"",

        },
        // we can build our schema or use or pre-built schema
        validationSchema:taskSchema,
        onSubmit: (values) => {
            console.log(values);
        }
    });

```
3- 
     in return form : we use handleSubmit and we use formik.values and formik.handleChange in every input
     also we should set id for each input
```
    <form onSubmit={formik.handleSubmit}>
        <div className="mb-2">
            <label for="Title" className="form-label col-form-labe">عنوان
            </label>
            <input
                id="Title"
                name="Title"
                type="text"
                id="Title"
                className="form-control"
                // value={task.Title}
                value={formik.values.Title}
                placeholder="عنوان"
                  // required={true}
                // onChange={onTaskChange}
                onChange={formik.handleChange}
                
            />
            
        </div>

 ```
 4- show ech errors below of input:

```
 <div className="mb-2">
  <label for="Description" className="form-label col-form-labe">توضیحات 
  </label>
      <input
          id="Description"
          name="Description"
          type="textarea"
          className="form-control"
          // onChange={onTaskChange}
          // value={task.Description}
          value={formik.values.Description}
          onChange={formik.handleChange}
          
      />
        {formik.errors.Description ? (<div className="text-danger">{formik.errors.Description}</div>): null}   
  </div>

```
5- 
با وارد کردن یک کارراکتر در اولین input همه خطاها نمایش داده می شود.
اما ما می خواهیم که وقتی روی هر input هستیم خطای مربوط به ان input نمایش داده شود : از onBlur برای هرinput استفاده می کنیم :
```
  <div className="mb-2">
                            <label for="Title" className="form-label col-form-labe">عنوان
                            </label>
                            <input
                                id="Title"
                                name="Title"
                                type="text"
                                className="form-control"
                                // value={task.Title}
                                value={formik.values.Title}
                                placeholder="عنوان"
                                  // required={true}
                                // onChange={onTaskChange}
                                onChange={formik.handleChange}
                                onBlur={formik.handleBlur}
                               
                            />
                           {formik.touched.Title && formik.errors.Title ? (<div className="text-danger">{formik.errors.Title}</div>): null}
                        </div>
```
6 - 
بعد از submit کردن باید createTask را هم فراخوانی کنیم :
```
    const formik = useFormik({
        initialValues : {
            Title:"",
            Category:"",
            Priority:"",
            Color:"",
            Description:"",

        },
        // we can build our schema or use or pre-built schema
        validationSchema:taskSchema,
        onSubmit: (values) => {
             console.log(values);
            createTask(values);
        }
    });
```

7- دیگر تابع createTaskForm ورودی event را نمی گیرد بلکه values را می گیرد :
```
const createTaskFrom = async(values) => {
    // event.preventDefault();
    try {
      setLoading((prevLoading) => !prevLoading);
     
      // await taskSchema.validate(task,{abortEarly:false});

      const {status,data} = await createTask(values) ;
      console.log('data:');
      console.log(data);
      console.log(status);
      if(status ===200){
        const allTasks= [... tasks,data];
        setTasks(allTasks);
        setFilteredTasks(allTasks);
        // setTask({});
        // setErrors([]);
        setLoading((prevLoading) => !prevLoading);
        navigate("/tasks");
      }
    } catch (error) {
      console.log(error.message);
      console.log(error.inner);
      // setErrors(error.inner);
      setLoading((prevLoading) => !prevLoading);
    }

  }
```

8- به جای فیلدهای value,name,onBlur,onChange در فرم وقتی از formic استفاده می کنیم می توانیم فقط با یک خط کد انجام دهیم:

```
<div className="mb-2">
    <label for="Title" className="form-label col-form-labe">عنوان
    </label>
    <input
        id="Title"
        type="text"
        className="form-control"
        placeholder="عنوان"
        {... formik.getFieldProps("Title")}
        
    />
```
9- می توانیم از کامپوننتFormik به چای useFormik استفاده کنیم :

کل تگ form داخل تگ های Formik می گذاریم :
```
  <Formik 
                    
      initialValues = {{
          Title:"",
          Category:"",
          Priority:"",
          Color:"",
          Description:"",

      }}
      
      validationSchema={taskSchema} 
      onSubmit= {(values) => {
          createTask(values);
      }}
   
      >
        {
            (formik) => (
            <form onSubmit={formik.handleSubmit}>
            ...
            </form>)
        }
  </Formik>
```

10 - برای ساده تر شدن حتی می توانیم از تگ Form خود Formik استفاده کنیم به شکل زیر :

ابتدا باید import کنیم :

```
import { Formik ,Form,Field,ErrorMessage} from "formik";
```

تغییر فرم به شکل زییر :
تبدیل id به name 
```
 <Form >
    <div className="mb-2">
        <label for="Title" 
        className="form-label col-form-labe">
        عنوان
        </label>
        <Field
            name="Title"
            type="text"
            className="form-control"
            placeholder="عنوان"
          
        />
         <ErrorMessage name="Title" render={(msg)=> (<div className="text-danger"> {msg}</div>)} />
    </div>

       <div className="mb-2">
          <label for="Category" className="form-label col-form-labe">دسته بندی
          </label>
              <Field
              
              name="Category"
              as="select"
              className="form-control"
              
              >
              <option value="">انتخاب دسته بندی </option>
              {categories.length > 0 &&
              categories.map((c)=>(
                  <option key={c.Id} value={c.Id}>{c.Title}</option>
              ))}
              </Field>
              <ErrorMessage name="Category" render={(msg)=> (<div className="text-danger"> {msg}</div>)} />
              </div>
```

