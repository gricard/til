# Use exact versions

My preference when dealing with npm packages is to use exact versions in package.json in order to maintain a deterministic build process.
If you want to set this as the default behavior when using [bun](https://bun.sh/), you can add this to your project's `bunfig.toml` file:

```toml
[install]
exact = true
```