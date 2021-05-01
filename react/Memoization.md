# Memoization in React

A great gist by [mrousavy](https://gist.github.com/mrousavy/0de7486814c655de8a110df5cef74ddc) covering most of the scenarios that require momoization. React Native has its own specific reasons for memoization.

## useCallback vs useMemo

`useCallback` gives referential equality between renders for __functions__. And `useMemo` gives referential equality between renders for __values__.

The following two snippets are equivalent,
```js
useCallback(fn, deps)
```
```js
useMemo(() => fn, deps)
```

## References
1. https://janhesters.com/usecallback-vs-usememo