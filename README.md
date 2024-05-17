# React Interview Question
1. ``` React Hooks ```
   - useState
     -  ```useState``` is a hook in React that allows functional component to manage state.
     -  it takes an inital state as an arugument and returns an array with two elements.
     -  the current state value and a function to update that value
     ```
     import React, {useState} from 'react';
     function Counter() {
        const [count, setCount] = useState(0);
        return (
        <div>
           <p>You clicked {count} time</p>
           <button onClick={() => setCount(count + 1)}>Click Me</button>
        </div>
        );
     }
     ```
   - useEffect
     - ```useEffect``` is another hook in React used for handling side effects in functional components.
     - it allows you to perform side effects in your function components, sunch as data fetching, subscriptions or manually changing the DOM after the components has rendered.
     - ```useEffect``` is called after every render
     - if you only want the effect to run once (similar to ```componentDidMount``` in class components) you can pass an empty dependency array [] as the second argument to useEffect.
     - if you want to pass dependencies for the effect you can pass them as an array to the second argument.
     - this prevents unnerssory re-calculations, improving performance.
     ```
          import React, { useState, useEffect } from 'react';
          function Example() {
            const [count, setCount] = useState(0);
             useEffect(() => {
                document.title = `You clicked ${count} times`;
             });
          return (
            <div>
                <p>You clicked  {count} times </p>
                <button onClick={() => setCount(count + 1)} > Click me </button>
             </div>
          );
          }
       ```
   - useContext
        - ```useContext``` is a hook in React that allows functional component to consume context that has been created using the ```React.createContext``` API.
        - It provides a way a to access the value of the nearest context of a specified type
          ```
             import React, {useContext} from 'react';
             //Create a context
             context ThemeContext = React.createContext('light');

             function ThemedButton() {
                const theme = useContext(ThemeContext);
                return <button style={{background: theme}}>Theme Button</button>
             }

             function Toolbar() {
                return (
                   <div>
                      <ThemedButton />
                   </div>
                );
             }

             function App() {
                return (
                   <ThemeContext.Provider value="dark">
                      <Toolbar />
                   </ThemeContxt.Provider>
                );
             }
          ```
   - useReducer
   - useMemo
     - ```useMemo``` is a hook in React used for memoization. which is a technique to optimize performance by caching the results of expensive function calls and reusing them when the
        input are the same .
      - it takes a function and an array of dependencies, and returns a momoized value.
        ```
           import React, {useState, useMomo } from 'react';
           function ExpensiveCalculation({a, b}) {
              const result = useMemo(() => {
                 console.log('Calculating....');
                 retun a*b;
              }, [a,b]);

              return(
                 <div> The result is : {result}</div>
              );
           }
        ```
   - useCallback
   - useRef
     - ```useRef``` is a hook in React that provides a way to persist mutable values across renders without causing a re-render when the value changes.
     - it returns a mutable ref object whose ```.current``` property is initialized to the passed argument ( this initial value)
     - The returned object will persist for the full lifetime of the component.
       ```
          import React, {userRef} from 'react';
          function TextInputwithFocusButton() {
             const inputEl = useRef(null);
             const onButtonClick = () => {
                inputEl.current.focus();
             };

          return (
             <div>
                <input ref={inputEl} type="text">
                <button onClick={onButtonClick}>Foucs the Input</button>
             </div>
          );
          }
       ```
2. Higher Order Component
   - What
   - When
   - How
   - Why
   - Exaple
3. Life Cycle method
   - Mount
   - Update
   - Un Mount
4. State Management
   - State
        - The state is a built-in React object that is used to contain data or information about the component. A component's state can change over time; whenever it changes, the                   component re-renders.
   - Props
        - Props are used to pass data from a parent component to a child component, while state is used to store data that can change within a component
   - Props Drilling
        - Props Drilling is a practice in which a prop or data is passed from one parent component to one or lower children's components, resulting in multiple levels of the component             tree
   - context
        - Context provides a way to pass data through the component tree without having to pass props down manually at every level
5. Redux / Zustand
   - How
   - why
   - when
   - Redux Toolket (RTK)
6. Custom Hooks
   - when
   - Example
7. Lazy Loading
   - Code Spliting
   - Chunking
8. Virtual DOM
   - Reconcilation
        - React Reconcilation is the process throught wich React update the Browser DOM. It makes the DOM updates faster in React.  It updates the virtual DOM first and then uses the             diffing algorithm to make efficient and optimized updates in the Real DOM
   - Render
        - Render is the technique that can redirect a page with the help of function render().
   - Differ Algoritham
        - The diffing algorithm's task is to identify the differences between the old and new Virtual DOM.
        - Instead of re-rendering the entire webpage, only the elements that have changed are updated in the real DOM.
   - How Render Works
        - The render method in the App component returns a React element (the h1 element). The ReactDOM. render function then takes this React element and renders it into the DOM node             with the id 'root
9. Server Sider Rendering (SSR) vs Client side Rendering (CSR)
    - how
    - Differrence
10. Routing (RBAC - Role base access control)
    - Product Route
11. Asyn Task
    - API Calls
    - Events
    - Promise / Fetch
    - Async await
12. Reusability
13. modularity
14. Testability
15. Performance
   - shimmer ui
   - Bundler
   - CDN
   - Optimize code
16. useDeferredValue
     - The `useDeferredValue` hook in React allows you to postpone updating a component of the UI. This can be beneficial for boosting performance when rendering a specific section of the UI is expensive, or when you wish to prioritize rendering other parts of the UI.
     - The useDeferredValue hook takes two arguments:

         - value: The value you want to defer. It can have any type
         - options: An object that can have the 2 properties timeoutMs and schedular
         - timeoutMs: The time in milliseconds to wait before updating the value.
         - scheduler: A function that will be used to schedule the update.
       Here are some of the benefits of using the useDeferredValue hook:

      - It can improve the performance of your application by preventing unnecessary re-renders.
      - It can help to improve the user experience by ensuring that the UI is always up-to-date.
      - It is easy to use and understand.
