
## virtual dom
یک شی درخت مانند هست که به React در واقع نقشه راه را نشان می دهد..در واقع نقشه نحوه برزو رسانی dom اصلی را نشان می دهد.
 dom اصلی html هست اماvirtual dom  از نوع js هست.. 
 

 دلیل سرعت بالای React : ابتدا چک می کند که vitual dom چه تغییری کرده است .. آن را اعمال می کند. سپس ان را با dom اصلی مقایسه می کند و دقیقا همان جایی که  باید تغییر کند را تغییر می دهد.  در حالیکه در کتابخانه های گذشته مانند jquery برای هر تغییر در صفحه کل dom دوباره ساخته می شد.

 پس وقتی قسمتی از web applicaton تغییر می کند مثلا روی دکمه ای کلیک می کنیم. ابتدا state تغییر می کند. سپس با   این تغییر react واکنش نشان می دهد بسته به تغییر و state جدید ، کامپوننت ها ادغام می شوند.. سپس طبق روال گفته شده Dom تغییر می کند. این همان جریان داده یک طرف هست.
 ## JSX
 به ساختار html مانند داخل کامپوننت ها گفته می شود. در JSX ما html را داخل javascript قرار می دهیم.
 
 JSX stands for JavaScript syntax extension. It is a JavaScript extension that allows us to describe React's object tree using a syntax that resembles that of an HTML template. It is just an XML-like extension that allows us to write JavaScript that looks like markup and have it returned from a component.

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
##
## کتابخانه های مرتبط
 ### React Native
 ساخت اپلیکشن های موبایلی
 ### Electron
 ### React Desktop
 ساخت اپلیکیشن ها تحت دسکتاپ
 ### REact 360 : 
 اپلیکیشن های VR 
 ### babel
  برای تبدیل سینتکس جدید js به سینتکس قدیمی js تا بتواند روی همه مرورگرها اجرا شود. این کتابخانه می تواند jsx را به javascript تبدیل کند. توسط سایت babel می توانیم تست کنیم.
 



## React Hooks
### useRef
برای فراخوانی یک عنصر در DOM استفاده می شود.
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
 هر بار که یک state تغییر کند، یک افکت ایجاد می‌کند.
 
### useContext

### useReducer
### useCallBack 
یک تابع رو میگیره و اون رو کَش میکنه یا به نوعی تو مموری ذخیرش میکنه و به ما تحویل میده.
### useMemo 
عملکرد این هوک هم شبیه به useCallBack هست با این تفاوت که به جای یک تابع یک مقدار memoized شده رو برمیگردونیم .
### useImperativeHandle 
برای ویرایش یک Ref در کامپوننت پدر استفاده می شود.

### useLayoutEffect 
این هوک شبیه به useEffect هست ولی useLayoutEffect قبل از این که صفحه render بشه و به کاربر نمایش داده
### useDebugValue 
برای دیباگ یک فانکشن استفاده میشود و زمانی اجرا میشه که React DevTools باز باشه .
### useDeferredValue 
این هوک یک مقدار رو میگیره و یه کپی از اون برمیگردونه

### useTransition 

### useId 
برای آیدی های یونیک استفاده میشه.
### useSyncExternalStore 
 
 برای وقتی استفاده میشه که قراره از یه منبع خارجی یک سری دیتا بخونیم
### useInsertionEffect 
عملکردی مثل useEffect داره با این تفاوت که قبل از این که DOM اجرا شده باشه عمل میکنه

## Tools
- [eslint-plugin-react-hooks](https://www.npmjs.com/package/eslint-plugin-react-hooks)
- Create React App (CRA) : 

برای این توسط توسعه دهندگان ساخته شده که برنامه نویسان React با یک دستور همه پکیچ های لازم را نصب کنند و در واقع یک پروژه React ایجاد کنند.

npm -i g create-react-app@5.0.1         or   npm -i g create-react-app@latest
- Vite

توسعه دهندگان حرفه ای استفاده می کنند.


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

## Services in React
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
## Loading show
```
// در کامپوننت یا فایل مورد نظر
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