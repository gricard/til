# Same component at the same position preserves state

Regardless of how your JSX code is structured, if your component renders the same type of component in the same position in the render tree, it will have access to the same state.
You can have entirely different blocks of logic in the component, like below, and each way it's rendered the `<Counter />` component will have the same state values.

If you rendered a different type of component as a child of the `<div>` then the state would be wiped out.

```jsx
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);
  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}

function Parent({hasMoreStuff}) {
    if (hasMoreStuff) {
        return (
            <div>
                <Counter/>
                <div>More stuff</div>
            </div>
        );
    }
    
    return (
        <div>
            <Counter/>
        </div>
    );
}
```

[React Docs](https://react.dev/learn/preserving-and-resetting-state#same-component-at-the-same-position-preserves-state)

The position includes the types of elements in the tree as well, not just the topological location.
If you change the type of a component/element in the tree, then it resets the state for its children also.

```jsx
function Parent({isSection}) {
    if (isSection) {
        return (
            <section>
                <Counter/>
            </section>
        );
    }
    
    return (
        <div>
            <Counter/>
        </div>
    );
}
```

