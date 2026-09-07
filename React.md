# React Interview

| Question |   | Question |   | Hook|
|----------|---|----------|---|---|
| [React](#react) | |[JSX](#jsx) | |[Hooks](#hook)|
|[Pure Components](#pure-components) | |[props/state](#propsstate) ||[useState](#usestate)|
|[React.memo()](#reactmemo) | |[Prop Drilling](#prop-drilling) ||[useEffect/useLayoutEffect](#useeffectuselayouteffect)|
|[Higher Order Component](#higher-order-component) | |[Controlled and Uncontrolled components](#controlled-and-uncontrolled-components) ||[useRef](#useref)|
|[Class and Functional Components](#class-and-functional-components) | |[React Router](#react-router) ||[usecallback](#usecallback)|
|[Strict Mode](#strict-mode) | |[Fragments and normal div](#fragments-and-normal-div) ||[useMemo](#usememo)|
|[Lazy Loading](#lazy-loading) | |[Optimize React Code](#optimize-react-code) ||[useReducer](#usereducer)|
|[Reconciliation](#reconciliation) | |[Custom Hook](#custom-hook)||[useActionState](#useactionstate)|
|[Virtual DOM and Real DOM](#virtual-dom-and-real-dom)| |[Life cycle method of components](#life-cycle-method-of-components) ||[useDebugValue](#usedebugvalue)||
|[key](#key)| |[Redux](#redux) ||[useTransition](#usetransition)|
|[Memoization in react](#memoization-in-react) ||[Event in react](#event-in-react) | |[useFormStatus](#useformstatus)|
|[Render and Re-render](#render-and-re-render)||||[Context API](#context-api)|

## React
React is an open-source front-end JavaScript library for building user interfaces based on components. It's used for handling the view layer in web and mobile applications, and allows developers to create reusable UI components and manage the state.

[⬆ Back to Top](#React-Interview)

## JSX
JSX stands for ```JavaScript XML```. It is a syntax extension for JavaScript that is commonly used in React to describe what the user interface should look like. JSX allows developers to write HTML-like code inside JavaScript, making React components easier to read and understand. Browsers do not understand JSX directly, so tools like ```Babel compile``` it into regular JavaScript, such as ```React.createElement()``` calls. JSX is not exactly HTML, although its syntax is similar to HTML.

[⬆ Back to Top](#React-Interview)

## Pure Components
```Pure Components``` is a component that:
<br/>✔️ Renders the same UI for the same props and state
<br/>✔️ Avoids unnecessary re-rendering by implementing a shallow comparison of props and state

###### In class use ```React.PureComponent```
```js
class MyPureComponent extends React.PureComponent {
  render() {
    console.log("Rendered!");
    return <h1>{this.props.title}</h1>;
  }
}
```
## React.memo()
used to memoize function component. It prevents a component form re-rendering if it's props haven't changed.

###### In function use ```React.memo```
```js
const MyPureFunction = React.memo(({ title }) => {
  console.log("Rendered!");
  return <h1>{title}</h1>;
});
```

[⬆ Back to Top](#React-Interview)

## Props/State
```props``` are inputs passed from a parent component to a child component. It is read only.

```state``` is internal data managed inside a component. we can change data. When state changes → component re-renders

[⬆ Back to Top](#React-Interview)

## Prop Drilling
```Prop Drilling``` is the process of passing data from a parent component to deeply nested child component by passing it through intermediate component, even if those component don't need the data themselves.

[⬆ Back to Top](#React-Interview)

## Virtual DOM and Real DOM
```Virtual DOM``` on the other hand, is lightweight copy of the real DOM that React keep in memory. when the ```state``` of a component changes, React first ```update the virtual DOM```. It the compares the **new virtual DOM with the previous one**(this is called diffing algothim) and calculates the most efficient way to update the real DOM.

```Real DOM``` is the actual DOM provided by ```the browser```. It re-presents the UI of the application, and gets update whenever the state of the application changes. However, update the real DOM is relatively slow, especially when dealing with frequent or complex changes.

[⬆ Back to Top](#React-Interview)

## Higher Order Component
```Higher Order Component``` a function that takes a component and return a new component with added functionality. HOC are used for re-using component logic and echancing components with additional behavior.

[⬆ Back to Top](#React-Interview)

## Controlled and Uncontrolled components
```Controlled components``` is a from form elements like Input or Textarea where the values is controlled by ```React State```. That menas the components data is stored in the state, and every user input udpate the state using ```onChange```. This give full control over the form data.

```Uncontrolled components```  on the other hand, manage it's own internal state. Instead of using ```React State```. we access the value using a ```ref```. These are more like traditional HTML form elements.

[⬆ Back to Top](#React-Interview)

## Class and Functional Components
```Class components``` are ```ES6``` classes that extend ```React.Component``` and must use ```this``` to access props, state and lifecycle method like **componentDidMount**, **return**, etc

```Functional components``` are just JS functions. They are the modern and recommended way to write React component, but with the **introduction of Hooks**(like useEffect, useState) they can manage state and side effect.

[⬆ Back to Top](#React-Interview)

## React router
React Router is a library for handling ```routing``` in react-applications. It allows you to navigte between different views or components in a **single-page application(SPA)** without need for a full page reload. React Router helps you can manage **URL** and **Browser Histary** while keeping the UI in sync with the URL.

[⬆ Back to Top](#React-Interview)

## Strict Mode
```Strict Mode<React.StrictMode>``` in React is a development tool that helps identify potential problems like- side effects, legacy API usage or unsafe lifecycle methods. It doesn't render anything to the UI and doesn't impact the production build, but it's extremely useful for writing clean and future-proof react code.

[⬆ Back to Top](#React-Interview)

## Fragments and normal div
```React Fragments``` is a lightweight wrapper that allows you to group multiple elements without adding extra nodes to the DOM. If you are using **React.Fragment** to render a list of items, you should use the ```key``` attribute.

```normal <div>``` Creates an actual DOM node. which can cause unnecessary extra nesting. May affect css layout or styling, especially in complex components where layout depends on create DOM structure.

[⬆ Back to Top](#React-Interview)

## Lazy Loading
```Lazy Loading``` in react means loading components only when they are needed, instead of loading everything at once during the initial load. It help's improve performance and reduce the bundle size. 
```jsx
import React, { lazy, Suspense } from "react";

const About = lazy(() => import("./About"));

function App() {
  return (
    <Suspense fallback={<div>Loading...</div>}>
      <About />
    </Suspense>
  );
}
```
**explain**-> we use ```React.lazy()``` to defined the component and wrap it with ```<Suspense>``` to show a fallback while the component is being loaded.

[⬆ Back to Top](#React-Interview)

## Optimize React Code
React code can be optimized by avoiding unnecessary re-renders, using memoization(**React.memo,useMemo,useCallback**), Lazy loading components, using keys properly in lists, optimizing state management and using tools like **Redux**.

[⬆ Back to Top](#React-Interview)

## Reconciliation
Reconciliation in react is the process of updating the DOM when the state or props of component change, React uses a virtual DOM to compare the old and new versions of the UI and update only the parts that changed, making it fast and efficient.

so there are **4-step in reconciliation**->
- **1. Component update**-> when state or props change, React re-renders the component.
- **2. Virtual DOM Diffing**-> React creates a new virtual DOM tree and compares it with the previous one.
- **3. Efficient update**-> It uses a diffing algorithm to find the differences.
- **4. DOM patching**-> Only the changed elements are update in the real DOM.

[⬆ Back to Top](#React-Interview)

## Custom Hook
Custom hook are functions that allow you to **reuse logic** that in values React's build-in hooks. They improve code reusability, keep components clean and follow the same rules as build in hooks. **For example** you can create a **useFetch hook** for fetching data or **useCounter hook** to manage counter logic.

[⬆ Back to Top](#React-Interview)

## Hook
- React Hook are special function that let you use React Features like **state and life cycle method** inside functional components.
- Before Hook, only class components could manage state and lifecycle, but Hooks make functional components just as powerful and easier to write.

**common hook are ->**
  
### useState
  ```useState``` hook lets us define a ```state``` for a ```function component```. The state variable name can be directly used inside the HTML.
  ```jsx
import { useState } from "react";
const [state, setState] = useState(initialValue);
```

[⬆ Back to Top](#React-Interview)

### useEffect/useLayoutEffect
```useEffect``` hook that lets you perform side effects in ```function component```.
useEffect runs after the component renders and after the browser paints the UI.

**dependency** array of ```useEffect```
  - **1. No Dependency Array** || Component Render -> useEffect runs -> State changes -> Component Re-render -> useEffect runs again
  - **2. Empty Dependency Array [] ⭐** || Component Mount -> Render -> useEffect runs
  - **3. Dependency with a Value [count]** || Initial Render -> useEffect runs ->count changes -> Component Re-renders -> useEffect runs again
  
  - **Use Cases:** 
    - fetching data from API
    - changing the DOM directly
  ```jsx
import { useEffect } from "react";
useEffect(() => {function, [dependencies]);
```
```useLayoutEffect``` runs after the DOM updates but before the browser paints the screen.
```jsx
import { useLayoutEffect } from "react";
useLayoutEffect(() => {
  // DOM reading or DOM manipulation
}, []);
```
[⬆ Back to Top](#React-Interview)

### useRef
```useRef``` is commonly used for accessing DOM elements or storing values without causing re-renders.
  - **Use Cases:**
    - Accessing DOM elements
    - Keeping previous values
    - Avoiding unnecessary re-renders
```jsx
import { useRef } from "react";
const myRef = useRef(initialValue);
```

[⬆ Back to Top](#React-Interview)

### useCallback
```useCallback``` hook return's a **memoized callback function**. Think of memoization as caching value so that it does not need to be re-callculated. The usecallback hook only runs when one of it's **dependencies update**.
  - **Use Cases:**
    - passing function to memoized child components,
    - avoid re-creating function un-necessary
```jsx
import { useCallback } from "react";

const memoizedFunction = useCallback(() => {
  // function logic
}, [dependencies]);
```

[⬆ Back to Top](#React-Interview)

### useMemo
```useMemo``` is return a memoized value. Think of memoization as caching a value, so that it does not need to be re-calculated. The useMemo Hook only run when one of it's dependencies update.
  - **Use Cases:**
    - expensive calculation,
    - avoid unnessary re-renders,
    - stable dependencies
```jsx
import { useMemo } from "react";

const memoizedValue = useMemo(() => {
  return expensiveCalculation();
}, [dependencies]);
```

[⬆ Back to Top](#React-Interview)

### useReducer
```useReducer``` hook is similar to the ```useState``` hook. ```useReducer``` is a manage complex state logic.
  - **Use Cases:**
  - state logic is complex
  - Many updates depend on previous state
```jsx //part1
const [state, dispatch] = useReducer(reducer, initialState);
```
**state → current state
dispatch(action) → triggers state update
reducer(state, action) → returns new state**
```jsx //part2
function reducer(state, action) {
  switch(action.type) {
    case "ACTION_TYPE":
      return newState;
    default:
      return state;
  }
}
```

[⬆ Back to Top](#React-Interview)

### useActionState
```useActionState``` is a Hook that allows you to update state based on the result of a form action.
    - ```jsx
      const [state, formAction, isPending] = useActionState(fn, initialState, permalink?);
      ```
    - Using information returned by a form action

[⬆ Back to Top](#React-Interview)

### useDebugValue
```useDebugValue``` is a React Hook that lets you add a label to a custom Hook in React DevTools.
  - ```jsx
    useDebugValue(value, format?)
    ```
  - ```jsx //example
    import { useDebugValue } from 'react';
    function useOnlineStatus() {
      // ...
      useDebugValue(isOnline ? 'Online' : 'Offline');
      // ...
    }
    ```

[⬆ Back to Top](#React-Interview)

### useTransition
```useTransition``` lets you mark **some state updates as non-urgent**, so React keeps the UI responsive while doing **expensive work in the background**.
  - ```jsx
    const [isPending, startTransition] = useTransition();
    ```
  - isPending → true while the transition is running
  - startTransition(fn) → wraps non-urgent updates

[⬆ Back to Top](#React-Interview)

### useFormStatus
```jsx
  const { pending, data, method, action } = useFormStatus();
```

[⬆ Back to Top](#React-Interview)

## Key
```Key``` help react identify, which element were added, changed or removed, key should be given to array element for providing a unique identity for each element. 

[⬆ Back to Top](#React-Interview)

## Memoization in react
Memoization is a way of caching the result of a function so that when the same input occur again, react can return the cached result instead of re-calculating.

**memeaization used-->**
1. avoid re-runnung expensive calculations
2. Improve app performance, especially for large or complex UI
3. prevent unnecessary re-renders of components

[⬆ Back to Top](#React-Interview)

## Event in react
React event are user interaction with the web-appication, such as **clicks, keyboard input, and other actions that trigger a response in the user Interface.

[⬆ Back to Top](#React-Interview)

## Life cycle method of components
A life cycle method in react is a special method that gets called at different stages of component's life. These stages include when a component is **created(mounted), update(re-renderd) or destoroyed(un-mounted)**
1. Mounting-> when component is create and added to the DOM.
2. Updating-> when component state or props change.
3. un-mounting-> when component is removed from the DOM.

**{How to use in Function component}**

we are using useEffect hook.
1. **mounting ->** useEffect(()=>{},[]) run once after mount.
2. **updating ->** useEffect(()=>{},[]) runs when dependencies change.
3. **un-mounting->** useEffect(()=>{return()=>{}},[]) cleanup in useEffect return function.

[⬆ Back to Top](#React-Interview)

## Redux
Redux is a state management library used to manage and share global application state.

#### Redux life cycle
1. Dispatch an Action
2. Action creators
3. Reducers
4. Store
5. UI/components

[⬆ Back to Top](#React-Interview)

## Context API
- Context API is a way to share global data in a React app without passing props manually through every component.
- It is mainly used for managing global data like theme, authentication, language settings, or user information.
- **It works using three main parts**:
  - **createContext()** – to create the context
  - **Provider** – to provide the data
  - **useContext()** – to consume the data in child components
- It solves the problem of **prop drilling**, where we pass props through multiple intermediate components that don’t actually use the data.

## Render and Re-render
```Render``` -> Rendering means React calls your component function to determine what the UI should look like.

```Re-render``` -> Re-render happens when React needs to calculate the UI again because something changed.
