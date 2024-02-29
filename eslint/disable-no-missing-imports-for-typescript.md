# Disable no-missing-imports for TypeScript

When using eslint with TypeScript, you will have errors generated for import statements like this that don't include the module type extension:

```javascript
import { User } from './models';
```

This is due to the `node/no-missing-import` rule conflicting with TypeScript.

Turn it off by adding this to your `.eslintrc` file:

```json
{
  "rules": {
    "node/no-missing-import": "off"
  }
}
```

and then add the [eslint-import-resolver-typescript](https://www.npmjs.com/package/eslint-import-resolver-typescript) package and put it in your eslint config.

[Reference](https://github.com/mysticatea/eslint-plugin-node/issues/248#issuecomment-1052550467)