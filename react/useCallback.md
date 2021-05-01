# React.useCallback() and React.Memo 

Every component in React has its state and some props passed by the parent component. A change in any of the both will trigger a rerender and the component goes through its update lifecycle. 

**Note:** Rerendering of a component does not only mean that the render function of the component will be called, but also that all the subsequent child components will re-render, regardless of whether their props have changed or not.

## React.Memo 
When we render a big list of elements, 

```jsx
import React from 'react';
import useSearch from './fetch-big-list';

function MyBigList({ term, onItemClick }) {
  const items = useSearch(term);
  const map = item => <div onClick={onItemClick}>{item}</div>;
  return <div>{items.map(map)}</div>;
}

export default React.memo(MyBigList);
```
We can use `React.memo` HOC (Higher Order Component) to _memoise_ the jsx output of the `MyBigList` function. So, basically, for a set of arguments passed to the function, we can store the output and resuse the same output for those set of arguments. 

But wait. Function are treated as first class citizens in JavaScript i.e. it can be stored in a variable, passed as an argument and can also be returned as an output from a function itself.

So if we pass a function to a memoised function, we have to make sure that we passing the same function reference else memisation would not work. But what the problem with passing functions as arguments or props in React? Everytime a functional component renders it creates a new reference for the functions defined in it. The callback function being passed to the child components won't be the same in subsequent re-renders causing memoization to fail.

```jsx
import React from 'react';

function MyComponent() {
  // handleClick is re-created on each render
  const handleClick = () => {
    console.log('Clicked!');
  };

  // ...
}
```
So, for the above example we have to make sure that the `onItemClick` callback function has the reference accross re-renders. React provides `useCallback` which can be used to wrap the function and let React know that the same reference has to be used accross re-renders. Optionally, we can pass in a dependency array as second argument if we want to create a new reference of the function when the dependency's value change.

```jsx
import React, { useCallback } from 'react';

function MyComponent() {
  // handleClick is the same function object
  const handleClick = useCallback(() => {
    console.log('Clicked!');
  }, []);

  // ...
}

```

**Note:**
We should not wrap every callback in useCallback. It only makes sense when it is being passed to a function or a compoent which has been memoised.



## Reference
1. https://dmitripavlutin.com/dont-overuse-react-usecallback/
2. https://reactjs.org/docs/hooks-reference.html#usecallback
3. https://reactjs.org/docs/hooks-reference.html#usememo
4. https://reactjs.org/docs/react-api.html#reactmemo