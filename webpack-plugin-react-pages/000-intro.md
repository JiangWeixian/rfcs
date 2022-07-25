- Start Date: 2022/07/25
- Implementation Repo: [(leave this empty)](https://github.com/JiangWeixian/webpack-plugin-react-pages)

# Summary

Webpack plugin port of vite-plugin-pages, provide file system-based react-routes for pure react project.

# Basic example

```tsx
import routes from 'virtual:react-pages'
import { useRoutes } from 'react-router'

const Routes = useRoutes(routes)
```

# Motivation

1. Make `react-template` project become better. 
2. Like `next.js` framework route convention. If anyone want to enable file-system based routes feature on pure csr project. There is one choose.

# Detailed design

1. use `vite-plugin-pages` directly, bundle it into dist files. make sure external `vite` related pages will not installed with `webpack-plugin-react-pages`
2. pass almost all options in `vite-plugin-pages`
3. use `webpack-virtual-modules` generate routes code
4. import routes from `virtual:react-pages`, startwith `virtual:` protocol
5. provide global types to make `virtual-module` type safe.
  
there is hmr issue with `webpack5` and `webpack-virtual-module`.

# Drawbacks

Currently, less and less developers will choose `csr`, or pure `webpack` react pages for side-project starter.

1. `nextjs`
2. `remix`
3. even `umi` is better choose

# Alternatives

Write raw react routes

# Unresolved questions

- [ ] in build mode, maybe should not clear cache before generate.
