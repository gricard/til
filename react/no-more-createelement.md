# No more createElement

We're not using React.createElement anymore. Not since before React 17. 
I've been thinking in terms of JSX being transpiled down to React.createElement calls forever. 
I never updated that thinking when React 17 came out.

It is now transpiled down to calls from `react/jsx-runtime` like this:

```javascript
import { jsx as _jsx } from "react/jsx-runtime";
import { jsxs as _jsxs } from "react/jsx-runtime";
function One() {
    const [s, setS] = useState(0);
    return /*#__PURE__*/_jsx("input", {
        value: s,
        onchange: e => setS(e.target.value)
    });
}
function Home() {
    const comp = /*#__PURE__*/_jsx(One, {});
    return /*#__PURE__*/_jsxs("div", {
        children: [comp, comp]
    });
}
```

Here's [the source](https://github.com/facebook/react/blob/main/packages/react/src/jsx/ReactJSXElement.js) to see how `jsx()` works

And here's [the discussion](https://github.com/reactjs/rfcs/blob/createlement-rfc/text/0000-create-element-changes.md#motivation) of the change and the reasons for it.