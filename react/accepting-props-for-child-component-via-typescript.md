# Accepting props for child component via TypeScript

If your component renders a second component as a child and you want to be able to accept any props that that component uses so you can pass them on, you can do it like this:


```tsx
import React from 'react';

const ChildComponent: React.FC<{
    name: string,
    age: number
}> = ({ name, age }) => {
    return (
        <div>
            <span>Name: {name}</span>
            <span>Age: {age}</span>
        </div>
    );
}

const ParentComponent: React.FC<React.ComponentProps<typeof ChildComponent>> = (props) => {
    return (
        <div>
            <span>{message}</span>
            <ChildComponent {...props} />
        </div>
    );
}

// and if the parent has other props...
const ParentComponent2: React.FC<{
    message: string
} & React.ComponentProps<typeof ChildComponent>> = ({ message, ...props }) => {
    return (
        <div>
            <span>{message}</span>
            <ChildComponent {...props} />
        </div>
    );
}
```