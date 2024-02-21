# Hidden Classes

This is an optimization feature for JS engines in web browsers.
When you create an object in JS, the engine generates optimized machine code for interacting with that specific object shape.
When this happens, the object has a hidden class associated with it, that links to that optimized code.
If you use many objects of that type, then they'll all use that optimized code.

But, if you change the object by adding/removing properties, it no longer fits that shape, and so the hidden class is removed, and you no longer have access to the optimized code.
If you're concerned about performance, then it is best to try and stick to defined object shapes and avoid arbitrary property changes.

Here are some links where you can further explore this type of optimization:

https://v8.dev/docs/hidden-classes
https://mathiasbynens.be/notes/shapes-ics
https://draft.li/blog/2016/12/22/javascript-engines-hidden-classes/
https://medium.com/@yanguly/inside-javascript-engines-part-2-code-generation-and-basic-optimizations-952bed02db62#:~:text=Hidden%20Classes