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

 ### 404 page
 ```
 <Switch>
  <Route exact path="/" component={Home} />
  <Route path="/user" component={User} />
  <Route component={NotFound} />
</Switch>
 ```


 ### redirect after login
 ```
 const Component = () => {
  if (isLoggedIn === true) {
    return <Redirect to="/your/redirect/page" />;
  } else {
    return <div>{"Login Please"}</div>;
  }
}
 ```