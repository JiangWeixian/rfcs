- Start Date: 2022/07/31
- Reference Issues: (fill in existing related issues, if any)
- Implementation PR: (leave this empty)

# Summary

If there are manay pages in project, project use reactr-router to import all `.tsx` files as react pages.
Webpack will compile all files at startup, it will waste long time.

In partial-compile mode, only active `location.pathname` matched react pages will be compiled, other react
pages will be filtered out.

# Basic example

in `webpack` config file,

```tsx
plugins: [
  new WebpackPluginReactPages({
    experiment: {
      enablePartialCompile: boolean
    }
  })
]
```

in project,

```tsx
import pages from 'virtual:react-pages'
```

# Motivation

In default, always compile all files under folder pages. It takes too much long time. However, maybe
only partial files or folder in develope mode will be used.

To reduce compile time in startup just like `nextjs` framework. Only active location matched react pages 
will be compiled.

# Detailed design

TODO

# Drawbacks

It should be job of webpack plugin?

# Unresolved questions

TODO