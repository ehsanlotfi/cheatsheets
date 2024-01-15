### چطوری یه کامپوننت رو هر ثانیه به روز کنیم؟
 ```
 const intervalRef = useRef();

useEffect(() => {
   intervalRef.current = setInterval(() => this.setState({ time: Date.now() }), 1000);

   return () => {
     clearInterval(intervalRef.current);
   }
}, [location]);
 ```