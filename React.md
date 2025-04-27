### React Hooks
###### 1- useState
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
- It's used to run special code during a component's lifecycle, like when the component mounts.
```
function FetchData() {
  const [data, setData] = useState([]);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/posts")
      .then((response) => response.json())
      .then((data) => setData(data));
  }, []); // It runs just once when the component is mounted.

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
- It’s used to manage global states, such as dark mode.
```
import React, { useContext, createContext } from "react";

const ThemeContext = createContext("light");

function DisplayTheme() {
  const theme = useContext(ThemeContext);
  return <p>Current theme: {theme}</p>;
}
```
###### 4- useRef
- It's used for accessing DOM elements.
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
- It works like useState but is better for complex states, and it changes the state through a `reducer` function.
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
###### 6- useMemo And useCallback
- They are used for caching and preventing unnecessary renders.
- useMemo is used to remember a calculated value so it only re-computes when certain dependencies change.
- in the below example will only recalculate number * 2 when number changes.
```
const result = useMemo(() => number * 2, [number]);
```
- useCallback is used to remember a function so it doesn’t get recreated on every render.
```
const handleClick = useCallback(() => { console.log('Clicked!'); }, []);
```
 
###### 8- useSearchParam
- It’s used to get URL parameters.
```
const [query, setQuery] = useSearchParam();
setQuery('page', 2);
```

###### 9- useLocation
- It’s used to access the current location.
```
const location = useLocation();
console.log(location.pathname); // "/home"
```

###### 10- useNavigate
- It’s used to route to another page.
```
const navigate = useNavigate();
navigate('/profile');
```

###### 11- useId
- create a uniqId.
```
const id = useId(); // :r1
return <label htmlFor={id}>Name</label>;
```

###### 12- useLayoutEffect
- It works like useEffect, but happens before the DOM renders.
```
useLayoutEffect(() => {
  console.log('DOM is ready');
});
```

###### 13- useInsertionEffect
- It applies styles before the render.
```
useInsertionEffect(() => {
  document.body.style.backgroundColor = 'blue';
});
```

###### 14- useImperativeHandle
- It’s used to handle a child reference from the parent component.
```
useImperativeHandle(ref, () => ({
  focus() {
    inputRef.current.focus();
  },
}));

```

###### 15- useTransition
برای مدیریت حالت های تاخیری در UI مثلا تا لیست محصولات میاد لودینگ ظاهر شود
```
function App() {
  const [list, setList] = useState([]);
  const [isPending, startTransition] = useTransition();

  const handleClick = () => {
    startTransition(() => {
      const newList = Array.from({ length: 10000 }, (_, i) => `Item ${i + 1}`);
      setList(newList);
    });
  };

  return (
    <div>
      <button onClick={handleClick}>Generate List</button>
      {isPending && <p>Loading...</p>}
      <ul>
        {list.map((item, index) => (
          <li key={index}>{item}</li>
        ))}
      </ul>
    </div>
  );
}
```
###### 16- useDeferredValue
برای به‌تأخیر انداختن بروزرسانی مقادیر سنگین.

###### 16- useDebugValue
برای دیباگ کردن هوک‌های سفارشی.

###### 17- useSyncExternalStore
همگام‌سازی با داده‌های خارجی.

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

### Reconciliation  (اصلاح ، آشتی)
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
```
// simple example of a Higher-Order Function in JavaScript

function applyOperation(a, b, operation) {
  return operation(a, b);
}

const add = (x, y) => x + y;
const multiply = (x, y) => x * y;

console.log(applyOperation(3, 5, add));        // Output: 8
console.log(applyOperation(3, 5, multiply));  // Output: 15
```

### Headless Component
کامپوننت Headless در برنامه‌نویسی (مخصوصاً در React) کامپوننتی است که فقط منطق را مدیریت می‌کند و هیچ رندر خاصی ندارد.

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

### shallow comparison  ( مقایسه سطحی )
وقتی که `props` یا `state` در کامپوننت تغییر‌می‌کنه، `PureComponent` یه مقایسه سطحی روی `props` و `state` انجام میده به این عمل `shallow comparison`  میگن.

### Synthetic events
وقتی شما در React یک رویداد مثل onClick تعریف می‌کنید، React به جای استفاده‌ی مستقیم از رویدادهای مرورگر، از چیزی به نام Synthetic Event استفاده می‌کند تا عملکرد یکسانی در تمام مرورگرها ارائه دهد.

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

### Fragment
- استفاده چندین المنت بدون افزودن نود اضافی
- key تنها اتریبیوتی هستش که میشه به Fragment پاس داد
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
گاهی اوقات نیاز دارید چیزی مثل مدال (Modal) یا نوتیفیکیشن (Notification) را بسازید که از نظر بصری و عملکردی خارج از بخش اصلی اپلیکیشن باشد. با استفاده از پرتال می‌توانید این کامپوننت‌ها را مستقیماً به یک بخش خاص در DOM (مثل <div id="modal-root">) اضافه کنید.
```
ReactDOM.createPortal(child, container);
```
- child: محتوایی که می‌خواهید نمایش دهید (مثلاً یک مدال).
- container: جایی در DOM که می‌خواهید محتوا آنجا رندر شود (مثل #modal-root).

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

### SSR in pure React
```
import ReactDOMServer from "react-dom/server";
import App from "./App";

ReactDOMServer.renderToString(<App />);
```

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

#### redux-thunk
-  اجازه میده بتونیم action‌های async داشته باشیم.
-  اجازه میده که actionهایی رو بسازیم که به‌جای action عادی تابع‌ برگردونن

#### redux saga
یک middleware برای مدیریت منطق جانب سرویس بصورت نخ های جداگانه (side effects) در اپلیکیشن‌های ریداکس است. 

##### put and call in react sega
هر دوی افکت‌های call و put سازنده‌های افکت هستن. تابع call برای ایجاد توضیح افکت استفاده میشه که به میان‌افزار دستور میده منتظر call بمونه. تابع put یه افکت ایجاد می‌کنه، که به store میگه یه action خاص رو فقط اجرا کنه.

### code-splitting
ویژگی پشتیبانی شده توسط باندلر‌هایی مثل webpack و browserify هستش که می‌تونه بسته‌های مختلفی ایجاد کنه که می‌تونه به صورت پویا در زمان اجرا بارگیری بشه.

### Imperative vs Declarative
- Imperative (دستوری): تمرکز روی چگونه انجام دادن (جزئیات).
- Declarative (بیانی): تمرکز روی چه چیزی انجام دادن (نتیجه).

یک دکمه لایک را در نظر بگیرید برای هندل کردن حالت های فعال و غیر فعال این دکمه دو تا راه حل وجود داره 
1. استفاده از یک کامپوننت و هندل کردن رنگ با if
2. استفاده از دو تا کامپوننت و هر رنگ جداگانه کامپوننت داشته باشد

# Hooks
- هوک ها فقط در ریاکت کامپوننت استفاده می شوند
- هوک‌ها رو فقط در ابتدای کامپوننت‌ها صدا کنیم.
- بوسیله کتابخانه eslint-plugin-react-hooks میتوانیم اطمینان حاصل کنیم از این شروط در پروژه ما اجرا شده.

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

### چرخه حیات در کامپوننت های تابعی

چرخه حیات در کامپوننت های تابعی توسط هوک useEffect انجام می گیرد

1- mount :
```
useEffect(() => { },[]);
```
2- update
```
useEffect(() => {}, [color]);
```
3- unmount
```
useEffect(() => { return() => { } },[]);
```
