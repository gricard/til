# Using Braces for Switch Cases

I think because I've generally avoided creating new variables inside of switch cases, I've just never encountered this before, but...
When you create variables with the same name inside multiple `case` blocks, the names will collide, since they're declared in the parent scope.
You can get around this by using braces in the `case` blocks to create a new scope.

I'm pretty sure I've gotten used to an `eslint` rule that yells at you when you create variables inside a `switch` and that's why I've never encountered this before.

```javascript
function getAnswer(thing) {
    switch (thing) {
        case 'no': 
            const answer = 'uh uh'
            return answer
        case 'yes': 
            // there will be an error here because `answer` is already declared
            const answer = 'uh huh'
            return answer
    }
}

function getAnswer(thing) {
    switch (thing) {
        case 'no': {
            const answer = 'uh uh'
            return answer
        }
        case 'yes': {
            // no problem here because it's in a different scope
            const answer = 'uh huh'
            return answer
        }
    }
}
```

I noticed this while reading the new [React docs](https://react.dev/learn/extracting-state-logic-into-a-reducer#step-2-write-a-reducer-function)