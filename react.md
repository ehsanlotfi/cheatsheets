
## virtual dom
یک شی درخت مانند هست که به React در واقع نقشه راه را نشان می دهد..در واقع نقشه نحوه برزو رسانی dom اصلی را نشان می دهد.
 dom اصلی html هست اماvirtual dom  از نوع js هست.. 
 

 دلیل سرعت بالای React : ابتدا چک می کند که vitual dom چه تغییری کرده است .. آن را اعمال می کند. سپس ان را با dom اصلی مقایسه می کند و دقیقا همان جایی که  باید تغییر کند را تغییر می دهد.  در حالیکه در کتابخانه های گذشته مانند jquery برای هر تغییر در صفحه کل dom دوباره ساخته می شد.

 پس وقتی قسمتی از web applicaton تغییر می کند مثلا روی دکمه ای کلیک می کنیم. ابتدا state تغییر می کند. سپس با   این تغییر react واکنش نشان می دهد بسته به تغییر و state جدید ، کامپوننت ها ادغام می شوند.. سپس طبق روال گفته شده Dom تغییر می کند. این همان جریان داده یک طرف هست.

 ### کتابخانه های مرتبط
 ## React Native
 ساخت اپلیکشن های موبایلی
 ## Electron
 ## React Desktop
 ساخت اپلیکیشن ها تحت دسکتاپ
 ## REact 360 : 
 اپلیکیشن های VR 
 



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
