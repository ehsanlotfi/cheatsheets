1. #### useState
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

1. #### useEffect
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

1. #### useContext
      - It’s used to manage global states, such as dark mode.
      ```
      import React, { useContext, createContext } from "react";

      const ThemeContext = createContext("light");

      function DisplayTheme() {
        const theme = useContext(ThemeContext);
        return <p>Current theme: {theme}</p>;
      }
      ```

1. #### useRef
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

1. #### useReducer
        - It works like useState but is better for complex states, and it changes the state through a `reducer` function.

1. #### useMemo And useCallback
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
 
1. #### useSearchParam
      - It’s used to get URL parameters.
      ```
      const [query, setQuery] = useSearchParam();
      setQuery('page', 2);
      ```

1. #### useLocation
      - It’s used to access the current location.
      ```
      const location = useLocation();
      console.log(location.pathname); // "/home"
      ```

1. #### useNavigate
      - It’s used to route to another page.
      ```
      const navigate = useNavigate();
      navigate('/profile');
      ```

1. #### useId
      - create a uniqId.
      ```
      const id = useId(); // :r1
      return <label htmlFor={id}>Name</label>;
      ```

1. #### useLayoutEffect
      - It works like useEffect, but happens before the DOM renders.
      ```
      useLayoutEffect(() => {
        console.log('DOM is ready');
      });
      ```

1. #### useInsertionEffect
      - It applies styles before the render.
      ```
      useInsertionEffect(() => {
        document.body.style.backgroundColor = 'blue';
      });
      ```

1. #### useImperativeHandle
      - It’s used to handle a child reference from the parent component.
            ```
            useImperativeHandle(ref, () => ({
              focus() {
                inputRef.current.focus();
              },
            }));
            ```

1. #### useTransition
      - lets you update the UI without blocking urgent interactions — it helps keep the app smooth during slow or heavy updates (e.g. loading page)
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
1. #### useDeferredValue
      - It's used to delay updating a heavy value.

1. #### useDebugValue
     -  It helps developers understand what a custom hook is returning when debugging.

1. #### useSyncExternalStore
     - Sync with external data.

1. #### Virtual DOM
      - Whenever the main data changes, the virtual DOM is compared with the real DOM, and the changes are applied.

1. #### Props vs State
      - The first refers to the inputs of a component, while the second refers to the variables inside a component.

1. #### Events in React and HTML
      - In HTML, event names are in lowercase, while in React they are in camelCase.
      - In HTML, to prevent the default behavior, we can use return, but in React, we must use preventDefault().
      - In HTML, parentheses are required, while in React, they are not mandatory.
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

1. #### Reconciliation
      - The literal meaning of `reconciliation` is when the state or props of a component change, React compares the newly returned element with the previously rendered one to decide whether a DOM update is really necessary. When these two values are not equal, React performs a DOM update. This process is called "reconciliation.

1. #### React Fiber
      - The new engine for reconciliation is essentially a reimplementation of the core React algorithm in version 16. The purpose of implementing React Fiber was to improve performance in areas like animations, working with layout, handling gestures, and providing the ability to pause, interrupt, or resume operations. It can also manage prioritization of necessary updates to the DOM. The most important feature of React Fiber is incremental rendering, which allows for chunking the execution process and pausing or resuming it across different frames.

1. #### set state for dynamic Model
      ```
      const [myState, setMyState] = useState();
      const handleInputChange = (event) => {
        setMyState({ [event.target.id]: event.target.value });
      }
      ```

1. #### lifecycle Class Component
      - Mounting `constructor,  getDerivedStateFromProps,  render,  componentDidMount`
      - Updating `getDerivedStateFromProps, shouldComponentUpdate,  render,  getDerivedStateFromProps,  componentDidUpdate`
      - Unmounting `componentWillUnmount`

1. #### lifecycle phases
      - Render
      - Pre-commit
      - Commit

1. #### getDerivedStateFromProps
      - After a component re-renders immediately without errors, the static method getDerivedStateFromProps is called. This method either returns an updated state as an object or returns null, which means that the new props do not require any state update.

      ```
      class MyComponent extends React.Component {
        static getDerivedStateFromProps(props, state) {
          //...
        }
      }
      ```

1. #### getSnapshotBeforeUpdate
      - After the DOM updates, this method is called. The returned value of this method is passed as the third parameter to the componentDidUpdate method.
      - The componentDidUpdate method covers everything that is used in the componentWillUpdate and componentWillReceiveProps methods.
      ```
      class MyComponent extends React.Component {
        getSnapshotBeforeUpdate(prevProps, prevState) {
          //...
        }
      }
      ```

1. #### HOC ( Hight Order Component )
      - A higher-order component (HOC) is essentially a function that takes a component as input and returns a new component with additional props or behaviors as output. For example, imagine you have a component that displays information about a person, and you want to modify this information based on the person's age. You could write an HOC that adds different features to the component depending on the person's age.
      - We can conditionally change the render behavior of a component using an HOC, a concept often referred to as "Render Hijacking.

1. #### What are the limitations of HOCs?
      - Don’t use HOCs inside the render method: Higher-order components (HOCs) should not be used inside the render method. Using HOCs in the render method can lead to unnecessary re-renders, which can hurt performance. It's better to apply them outside of the render flow.
      - Static methods need to be copied: When applying an HOC to a component, the new component doesn't inherit the static methods from the original component. If you want the static methods to be available on the new component, you need to manually copy them.
      - Refs cannot be passed down: Refs cannot be passed automatically through HOCs. If you need to forward a ref, you must use React.forwardRef in combination with your HOC.
      - We have the same concept in JavaScript, and it's called HOF (Higher-Order Function), which is a function that either takes another function as an input or returns a function as output.

      ```
      function applyOperation(a, b, operation) {
        return operation(a, b);
      }

      const add = (x, y) => x + y;
      const multiply = (x, y) => x * y;

      console.log(applyOperation(3, 5, add));        // Output: 8
      console.log(applyOperation(3, 5, multiply));  // Output: 15
      ```

1. #### Headless Component
      - A Headless component in programming (especially in React) is a component that only manages logic and has no specific rendering.

1. #### suspense component
      - When you want data or components to be loaded dynamically (Lazy), and during this time, show something like a "Loading..." text.
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

1. #### shallow comparison
      - When props or state in a component changes, PureComponent performs a shallow comparison on props and state. This action is called shallow comparison.

1. #### Synthetic events
      - When you define an event like onClick in React, React uses something called a Synthetic Event instead of directly using browser events to provide consistent behavior across all browsers.

1. #### Ref and ForwardRef
      - In class components, we use React.createRef, and in function components, we use the useRef hook.
    

1. #### props proxy in HOC
      - We can add or modify the props passed to a component using the props proxy pattern.
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

1. #### Fragment
      - Using multiple elements without adding extra nodes.
      - key is the only attribute that can be passed to a Fragment.
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

1. #### portal in React
      - Sometimes, you need to create something like a modal or notification that visually and functionally exists outside the main part of the application. With portals, you can directly add these components to a specific part of the DOM (like <div id="modal-root">).
        ```
        ReactDOM.createPortal(child, container);
        ```
       - child: The content you want to display (e.g., a modal).
       - container: The location in the DOM where you want the content to be rendered (e.g., #modal-root).

1. #### PropType
        - In development environments, it's useful for specifying the input type of a component. With TypeScript, you can also perform type checking to ensure that the correct types are passed to components.

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

1. #### error boundary
      - In class components, error boundaries are used and implemented with methods like componentDidCatch(error, info) and static getDerivedStateFromError.
      - In function components, error boundaries can't be used directly, and they are usually not needed. Instead, for most cases, an error boundary is defined for the entire application, which can be implemented with try...catch.

1. #### SSR in pure React
        ```
        import ReactDOMServer from "react-dom/server";
        import App from "./App";

        ReactDOMServer.renderToString(<App />);
        ```

1. #### Switcher Component
      - A component that can conditionally render multiple components based on certain conditions
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

1. #### StrictMode Tag
      - It doesn’t render any extra DOM element, but it enables warnings and extra checks for its child components. This only works in development mode.
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

1. #### constructor VS getInitialState 
      - When we use ES6 classes, we need to initialize the state inside the constructor. But when using React.createClass, we should use the getInitialState method.

1. #### super() VS super(props)
      - Outside the constructor, it doesn't matter. But if we want to access props inside the constructor, we must use super(props).

1. #### Loop in JSX
      - only Array.prototype.map OR for statement

1. #### setState Vs replaceState
      - Both are used in class components.
      - setState merges the current state with the new one.
      - replaceState completely replaces the current state with the new state.

1. #### State change Detection
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

1. #### component without HTML rendering
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
      - You can't work with a value that is undefined.

1. #### React router
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

1. #### Shallow Renderer package
      - It is used for writing unit tests, and allows you to deeply inspect a component one level at a time.
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

1. #### test Renderer package
      - We can use it to render components and turn them into pure JavaScript.
        This package lets us take a snapshot of the view hierarchy (similar to the DOM tree) created by ReactDOM or React Native, without needing a browser or jsdom.

1. #### Flux Architecture
      - An architecture proposed by Facebook that includes several main parts.
        - Action
        - Dispather
        - Store
        - View

1. #### Redux ( state managment )
      - Three Principles
        1.  Single source
        1.  State is read-only (only change by dispacher)
        1.  Changes are made with pure functions
      - Keyword
          - `store` is an object that holds all the states inside it.
          - `action` specifies what change should occur in the application state.
          - `reducer` takes the previous state and the current action and returns the new state.
          - `Containers` are components that don't have templates.
          - `Components` are components that have templates.
          - `selector` is used to select a part of the state.
      - Middleware 
          - Redux Thunk
            - It allows us to have async actions.
            - It allows us to create actions that return functions instead of normal actions.
          - Redux Promise
          - Redux Saga.
            - A middleware for managing side effects logic in Redux applications as separate threads.

1. #### put and call in react sega
      - Both call and put effects are effect creators. The call function is used to create an effect that instructs the middleware to wait for the call. The put function creates an effect that tells the store to execute a specific action.

1. #### React Style (CSS)
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

1. #### NOTES
      - If we update the state directly, our component will not re-render.
      - Callback methods in React are usually passed as the second parameter of hooks and can be executed after the hook operation is done.
      ```
      setState({ name: "John" }, () =>
        console.log("The name has updated and component re-rendered")
      )
      ```
      - The dangerouslySetInnerHTML feature is React's alternative to using innerHTML in the browser's DOM. Its functionality is similar to innerHTML, but using it carries a high risk of cross-site-scripting (XSS) attacks.

      - The CLI environment in React is called CRA, which stands for create-react-app.

      - If we use Template strings in the template, we must include the this keyword. If we use it normally, there is no need for it.
      ```
      <img className="image" src={"images/" + props.image} />

      <img className="image" src={`images/${this.props.image}`} />
      ```

      - To run the application with SSL, we use the following command.
      ```
      "scripts": {
        "start": "set HTTPS=true && react-scripts start"
      }
      ```

1. #### React Routing
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
              <h1>Main Page</h1>
              <button onClick={handleClick}>go to About</button>
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
              <button onClick={() => handleClick(123)}> go to page with id 123</button>
            </div>
          );
        }

        function User({ match }) {
          const { userId } = match.params;
          return (
            <div>
              <h1>User profile with ID {userId}</h1>
            </div>
          );
        }
        ```
        - The React Router framework is a wrapper around the history library, which manages actions on window.history using the hash and browser objects.

        - For multilingual support in React, we use the React-Intl library.
  
1. #### basic rules in JSX
        - If we want to use a CSS tag, we use className instead of class because class is a reserved word in JavaScript.
        - We must have a single root element. All the code should be inside one element, like the App element in React.
        - Comments cannot be placed like in HTML, instead, they must be written like JavaScript comments.

        ```
        {/*comment*/}
        ```
        - Every element we open must be closed. For example, if we want to use the <br> tag, we need to write it as <br />.
        - We can only use JavaScript inside JSX as an expression, such as using a loop or displaying the value of a variable.
 
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
1. #### key 
      - It is a string property used in lists. This property helps React detect changes and gives each item a unique identity and order.
      ```
      const ids = [1,2,3,4,5];
      const listElements = ids.map((id)=>{
          return(
              <li key={id.toString()}>{id}</li>
          )
      })
      ```

1. #### Lifecycle in Functional Components
      - The lifecycle in functional components is handled by the useEffect hook.
        1. mount 
        ```
        useEffect(() => { },[]);
        ```
        1. update
        ```
        useEffect(() => {}, [color]);
        ```
        1. unmount
        ```
        useEffect(() => { return() => { } },[]);
        ```
