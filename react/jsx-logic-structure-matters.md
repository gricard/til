# JSX Logic Structure Matters

It might seem like these two pieces of code are equivalent, but they result in different behaviors in regard to component state:

```jsx
function Example1({isFirstItem}) {
    return (
        <div>
            {isFirstItem ? <Input name="First" /> : <Input name="Second" />}
        </div>
    )
}

function Example2({isFirstItem}) {
    return (
        <div>
            {isFirstItem && <Input name="First" />}
            {!isFirstItem && <Input name="Second" />}
        </div>
    )
}
```

In `Example1` the two `Input` components take up the same position in the render tree, 
and since they are the same component type (and do not use a `key` prop to differentiate them), they will also reuse the same state. 

In `Example2`, it appears that it would be the same case, since you're only going to render one of those two `Input` components based on `isFirstItem`.
However, there are two separate JSX statements there, and when it's transpiled down, you end up with two children for that `div` instead of one, so they will never share the same state.

Here's how it looks when you transpile the code:

```javascript
function Example1({
  isFirstItem
}) {
  return /*#__PURE__*/_jsx("div", {
    children: isFirstItem ? /*#__PURE__*/_jsx(Input, {
      name: "First"
    }) : /*#__PURE__*/_jsx(Input, {
      name: "Second"
    })
  });
}

function Example2({
  isFirstItem
}) {
  return /*#__PURE__*/_jsxs("div", {
    children: [isFirstItem && /*#__PURE__*/_jsx(Input, {
      name: "First"
    }), !isFirstItem && /*#__PURE__*/_jsx(Input, {
      name: "Second"
    })]
  });
}
```

Notice how `children` in `Example1` is a single item, and in `Example2` it is an array of two items.

See [Same Component Same Position Same State](./same-component-same-position-same-state.md) for more details on this behavior.

