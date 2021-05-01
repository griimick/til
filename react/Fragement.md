# React.Fragment

JSX (Javascript Extended) is _compiled_ to raw Javascript. Every React component in JSX creates a corresponding `React.createElement()`. To see it in action, check out the [Babel REPL](https://babeljs.io/repl/#?presets=react&code_lz=MYewdgzgLgBApgGzgWzmWBeGAeAFgRgD4AJRBEAGhgHcQAnBAEwEJsB6AwgbgChRJY_KAEMAlmDh0YWRiGABXVOgB0AczhQAokiVQAQgE8AkowAUAcjogQUcwEpeAJTjDgUACIB5ALLK6aRklTRBQ0KCohMQk6Bx4gA) _(Read Eval Print Loop)_

## React.createElement()

createElement returns a new React Element of the given type. If we look closely, it returns `one` element and can have `multiple` child elements. 
```js
React.createElement(
    type,
    [props],
    [...children]
)
```

## How to return more than one element?

One way is that we can wrap the multiple elements in another element and call it the day. But this has its own disadvantages, we can screw up the HTML semantics. In the following example, we are adding `div` to wrap the `td` which is bad.
```jsx
<ul>
    {
        [{name: "One", type: "Type A"}, {name: "Two", type: "Type B"}].map((map, key) => (
            <div>
                <td>Item1.name</td>
                <td>Item1.type</td>
            </div>
        ))
    }
<ul>
```

`React.Fragment` to the rescue. We can use `React.Fragment` to wrap the multiple elements in a dummy React Element which does not show up in the actual DOM but rather ties the children together in the VDOM.

```jsx
<ul>
    {
        [{name: "One", type: "Type A"}, {name: "Two", type: "Type B"}].map((map, key) => (
            <React.Fragement>
                <td>Item1.name</td>
                <td>Item1.type</td>
            </React.Fragment>
        ))
    }
<ul>
```

**Note: **
`<></>` can also be used in place of `React.Fragment`. The only difference is that the shorthand syntax `<></>` does on accept any attributes like `key`.


References:
1. https://reactjs.org/docs/fragments.html
2. https://babeljs.io/repl
3. https://reactjs.org/docs/react-api.html#createelement