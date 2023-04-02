## React Hooks
### useRef
برای فراخوانی یک عنصر در DOM استفاده می شود.
### useState 
- معادل setState در کامپوننت های کلاس محور می باشد.
- برای ایجاد و ویرایش state ها در React مورد استفاده قرار میگرد
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

## Tools
- [eslint-plugin-react-hooks](https://www.npmjs.com/package/eslint-plugin-react-hooks)
