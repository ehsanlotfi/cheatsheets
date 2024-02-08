
## Tools
- [eslint-plugin-react-hooks](https://www.npmjs.com/package/eslint-plugin-react-hooks)
- Create React App (CRA) : 

برای این توسط توسعه دهندگان ساخته شده که برنامه نویسان React با یک دستور همه پکیچ های لازم را نصب کنند و در واقع یک پروژه React ایجاد کنند.

npm -i g create-react-app@5.0.1         or   npm -i g create-react-app@latest
- Vite

توسعه دهندگان حرفه ای استفاده می کنند.

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

کامپوننت فرزند:
```
CostomizedInput = (probs,ref) => {
  // has it`s own ref`
  cost inputRef= useRef();
  useImperativeHandle(ref,() = > ({
    focus: () => {
      inputRef.current.focus;
      alert('Hello');
    }
  }));
  return <input ref={inputFer} {...probs}/>;
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

- use  useEffect


ما می توانیم از چرخه حیات mount, unmount هم استفاده کنیم

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

### اعتبارسنجی فرم ها
برای اعتبارسنجی مقادیر input ها در فرم دو راه داریم :

1- خودمان شرط بنوسیم که مثلا حتما فیلدهای اجباری پر شده باشد برای فیلدهای عددی حتما عدد وارد شده باشد.

2- استفاده از کتابخانه Yup