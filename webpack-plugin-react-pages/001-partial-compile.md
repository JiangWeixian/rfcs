- Start Date: 2022/08/19
- Reference Issues: (fill in existing related issues, if any)
- Implementation PR: (leave this empty)

# Summary

Only compile currently pathname matched pages.

# Basic example

if project contain

```ts
- pages
  - about
  - day
```

visit `/day` only will compile `day.tsx`, and other default pages like `App.index`

in `webpack` config file,

```tsx
plugins: [
  new WebpackPluginReactPages({
    experiment: {
      partialCompile: boolean
    }
  })
]
```

in project,

```tsx
import pages from 'virtual:react-pages'
```

# Motivation

If project contain lots of pages, will make pull compile speed down.

# Detailed design

1. Step 1 - fetch `location.pathname` in devserver

2. Step 2 - filter routes by pathname

```ts
const routes = convention.glob()
const result = routes.filter(location.pathname)
```

write result into `virtual-module`


# Drawbacks

Why should we *not* do this? Please consider:

- implementation cost, both in term of code size and complexity
- whether the proposed feature can be implemented in user space
- the impact on users
- integration of this feature with other existing and planned features
- cost of migrating (is it a breaking change?)

There are tradeoffs to choosing any path. Attempt to identify them here.

# Alternatives

What other designs have been considered? What is the impact of not doing this?

# Adoption strategy

If we implement this proposal, how will existing users adopt it? Is
this a breaking change? Can we write a codemod? Can we provide a runtime adapter library for the original API it replaces? 

# Unresolved questions

Optional, but suggested for first drafts. What parts of the design are still
TBD?