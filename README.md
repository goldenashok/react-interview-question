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
      - Ref URL : https://www.youtube.com/watch?v=iDi0oAcpfG4&list=PLddu5tL-zt89qhynJUFnZedUmr7fJW0Xw&index=15
17. useTransition()
      - useTransition() can be used to tell React that certain state updates have a lower priority (i.e., all other state updates or UI rendering triggers have a higher priority).

      - When calling useTransition(), you get back an array with exactly two elements: An isPending boolean value, telling you whether the low-priority state update is still pending, and a startTransition() function that can be wrapped around a state update to tell React, that it is a low-priority update.
       ```
         import React, {useState, useTransition } from "react";
         import { ActivityIndicator, Button, SafeAreaView, Text, TextInput, TextInputComponent } from "react-native";
         const App =()=>{
         const [isPending, startTransition] = useTransition();
             const [count, setCount] = useState(0);
             
             function handleClick() {
               startTransition(() => {
                 setCount(count => count+ 1);
               })
             }
         return(
             <SafeAreaView
          style={{flex:1,alignItems:"center",justifyContent:"center"}}>
               
               {isPending && <ActivityIndicator />}
               <Text>{count}</Text>
                 <Button  title="Count" onPress={()=>handleClick()} />
         </SafeAreaView>)
         }
         export default App
      ```
       Ref URL : https://www.youtube.com/watch?v=hyDDerWv7mg&list=PLddu5tL-zt89qhynJUFnZedUmr7fJW0Xw&index=13
18. useTransition() vs useDeferredValue()
    - useTransition() -> Update the state Value
    - useDeferredvalue() -> Update the value

19. React Query
      React Query is a JavaScript library designed to simplify the complex task of data fetching and caching in React applications. It offers a set of hooks and utilities that enable you to manage data from various sources, including REST APIs, GraphQL, or even local state, effortlessly.
   ```
   import React from 'react';
   import logo from './logo.svg';
   import './App.css';
   import { useQuery, useMutation } from '@tanstack/react-query';
   
   function App() {
     const userData = useQuery(
       ['users'], 
       () => {
         return fetch('https://jsonplaceholder.typicode.com/users').then(response => response.json());
       },
       {
         enabled: false,
       }
     );
   
     const mutatePost = useMutation(
       ['posts'],
       (newPost: any) => {
         return fetch('https://jsonplaceholder.typicode.com/posts', {
           method: 'POST',
           body: JSON.stringify(newPost),
           headers: {
             'Content-type': 'application/json; charset=UTF-8',
           },
         }).then((response) => response.json())
       }
     )
   
     return (
       <div>
         <div>
           <button onClick={() => userData.refetch()}>Get Users</button>
           <div>
             {userData.isFetching && (
               <div>Fetching user data...</div>
             )}
             {userData.isError && (
               <div>{`Error get data!!!`}</div>
             )}
             {userData.data && userData.data.length > 0 && userData.data.map((user: any) => (
               <div>{user.name}</div>
             ))}
           </div>
         </div>
         <hr />
         <div>
           <button onClick={() => mutatePost.mutate({ title: 'First Post', body: 'First Post Body', userId: 1 })}>Add New Post</button>
           <div>
             {mutatePost.isLoading && (
               <div>Adding new post...</div>
             )}
             {mutatePost.isError && (
               <div>{`Error add new post!!!`}</div>
             )}
             {mutatePost.data && (
               <div>{`Success add new post with title : '${mutatePost.data.title}'`}</div>
             )}
           </div>
         </div>
       </div>
     );
   }
   
   export default App;
   ```
   - Difference between useQuery and useMutation
      - Purpose: useQuery is for reading data, while useMutation is for modifying data.
      - Typical Use Case: useQuery is used when you want to fetch and display data, while useMutation is used when you want to make changes to that data.
      - Return Values: useQuery returns { data, error, isLoading, isFetching }, while useMutation returns { mutate, data, error, isError, isLoading, isSuccess }.
      - Error Handling: Both hooks handle errors, but useMutation provides additional features for handling optimistic updates and rollbacks in case of errors during mutations.
        
