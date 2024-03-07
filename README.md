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
     - ```
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
        
   - useReducer
   - useMemo
   - useCallback
   - useRef
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
   - Props
   - Props Drilling
   - context
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
   - React Fiber
   - Render
   - Differ Algoritham
   - How Render Works
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
