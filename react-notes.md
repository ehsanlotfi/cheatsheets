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
##### What are the limitations of HOCs?
1. از HOC‌ها توی متد render استفاده نکنیم
2. متد‌های static باید کپی بشن وقتی HOC رو روی یه کامپوننت اعمال می کنیم، کامپوننت جدید هیچ کدوم از متد‌های استاتیک کامپوننت اصلی رو نداره
3. Ref‌ها رو نمیشه انتقال داد 


- همین مفهوم را در جاوااسکریپت هم داریم بهش میگیم `HOF ( Higher-Order Function )`
  که تابعی که یک تابع دیگه را به عنوان ورودی میگیره یا یک تابع را به عنوان خروجی return می کند

### Throttling vs Debouncing
در Throttling یک بازه زمانی وارد میکنیم در این بازه حداقل یکبار اجرا میشود
دومی بعد از آخرین اجرا یک ایونت یک بازه زمانی منتظر بمون بعد اجرا کن


### suspense component
اگه یه ماژول شامل import داینامیک باشه و هنوز رندر نشده نباشه، توی کامپوننت والدش باید یه رابط کاربری loading براش نمایش داده بشه. این بخش می‌تونه با کامپوننت Suspense مدیریت بشه. برای مثال کامپوننت‌های پایین رو ببینید که از Suspense در طول مدت بارگذاری کامپوننت دوم استفاده می‌کنن:
یک از جاهایی که میتونه استفاده بشه در routing است
```
const OtherComponent = React.lazy(() => import("./OtherComponent"));

function MyComponent() {
  return (
    <div>
      <Suspense fallback={<div>Loading...</div>}>
        <OtherComponent />
      </Suspense>
    </div>
  );
}
```


### formik Lib 
 یه کتابخونه ری‌اکت هست که امکان حل سه مشکل اساسی رو فراهم می‌کنه:
1. دریافت و مدیریت مقادیر از state
2. اعتبارسنجی و مدیریت خطا‌ها
3. مدیریت ثبت فرم‌ها
   

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

redux thunc vs redux-saga
هر دوی ReduxThunk و ReduxSaga می‌تونن مدیریت ساید افکت‌ها رو به دست بگیرن. توی اکثر سناریوها، Thunk از Promise استفاده می‌کنه، درحالیکه Saga از Generatorها استفاده‌می‌کنه. Thunk تقریبا ساده‌تره و promise رو تقریبا همه دولوپرها باهاش آشنا هستن، در حالی‌که Sagas/Generatorها خیلی قوی‌تر هستن و می‌تونن کاربردی‌تر باشن ولی خب لازمه که یاد بگیرینش. هردوی میان‌افزارها می‌تونن خیلی مفید باشن و شما می‌تونین با Thunks شروع کنین و اگه جایی دیدین نیازمندی‌تون رو برآورده نمی‌کنه سراغ Sagas برید.

##### put and call in react sega
هر دوی افکت‌های call و put سازنده‌های افکت هستن. تابع call برای ایجاد توضیح افکت استفاده میشه که به میان‌افزار دستور میده منتظر call بمونه. تابع put یه افکت ایجاد می‌کنه، که به store میگه یه action خاص رو فقط اجرا کنه.



#### mapStateToProps vs mapDispatchToProps 

### FLux ( state managment )
1. State can be changed
2. use multiple Store

### code-splitting
ویژگی پشتیبانی شده توسط باندلر‌هایی مثل webpack و browserify هستش که می‌تونه بسته‌های مختلفی ایجاد کنه که می‌تونه به صورت پویا در زمان اجرا بارگیری بشه.

### render hijacking
به معنی توانایی کنترل اینکه چه کامپوننتی خروجی بقیه رندر شدن یه کامپوننت دیگه باشه هست. در واقع ما می‌تونیم با قرار دادن کامپوننت خودمون توی یه کامپوننت با اولویت بالا(HOC) یه تغییراتی بهش بدیم، مثلا یه سری prop بهش اضافه کنیم یا تغییرات دیگه‌ای که باعث تغییر منطق رندر بشه. HOC در واقع hijacking رو فعال نمیکنه اما با استفاده از HOC این امکان رو فراهم می‌کنیم که کامپوننت بتونه رفتار متفاوتی رو موقع رندر داشته باشه.

### Imperative vs Declarative
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
  
