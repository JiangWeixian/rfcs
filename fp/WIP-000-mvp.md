- Start Date: 2022/03/02
- Reference Issues: (fill in existing related issues, if any)
- Implementation PR: (leave this empty)

# Summary

Module system in fp(shortname of flash-point, based on vite) framework

# Basic example

## glossy
> because plugin in rollup is build

- definePlugin - modify build config(rollup)
- defineModule - working in application

## usage

### development

```tsx
import { defineModule, definePlugin } from '@fp/kit'

// follows functional will inject provider or plugin filepath during build time
defineModule((api) => {
  // api.addProvider()
  // api.addPlugin()
})

// exec definePlugin callback during runtime
definePlugin(() => (api) => {
  // some codes
})
```

**in project**

```tsx
import { useContext, $ } from 'fp'

// useContext # load api from addProvider()
// addPlugin # modify vite build
```

**in config**

`fp.config.ts`

```ts
{
  // fp modules, contain rollup plugin and runtime component
  module: [
    pkg()
  ],
  // rollup plugins
  plugins: []
}
```

# Motivation

- react lack global variable define
- react lack module system

# Detailed design

## define plugin

`import { definePlugin } from 'fp/kit'`

`definePlugin` is typed-safe function, return defined plugin schema

example code

```ts
const module = definePlugin(define: Define)
```

`Define` should has similar fields like `rollup` plugins.

## define modules

### plugin ctx

`fp` new framework `instance` into `global-this`, it's better for

```ts
// bad
export const store = {}
// good
globalThis[app] = appinstance
appintance.store = {}
```

there are some reasons of why second way is better:

1. in `plugin-module` access flash-point instance by `useFlashpoint` from `plugin-context`, get `apis` module files by syntax like `context.apis`
2. in `defineModule` access flash-point instance by `useFlashpoint` from `plugin-context`

not required `import plugin-context from 'xxx/xxx'` 

### fp and vite lifetime

> **💡 NOTE**  
`fp` process `fp-modules` before `vite-plugins`

1. new app instance
2. new modules, exec modules
3. into `vite` lifetime

### hooks

builtin `hookable`

- in `cli`, hookable used for cli progress log
- in `app`, hookable used for lifetime

there are two kinds of hooks, one for build, another for app. *In build time, never call app-hooks*

## what module do

example code:

```tsx
// in plugin.mjs
export default definePlugin((fp) => {
  // codes
  fp.axios = axios
})
```

write nodejs api is not allowed here

### global context and apis

`providers`

1. in build time: read providers from `fp.providers` variables(added from `defineModule` with `api.addProvider`)
2. in application: compose provider into app-provider, make `app = appprovider(app)`

`apis`

same as `provider`

1. in build time: read store from `fp.apis` variables, (added from `defineModule` with `api.addAPIs`)
2. in application: `fp/apis` content is `stringify(fp.store variables)`

### usage

in project

```tsx
// store
import $ from 'fp/apis'
```

## complete demo

```tsx
// index.mjs
export default definePlugin({
  setup(api) {
    api.addProvider({ src })
  }
})

// module.mjs
export default defineModule((app) => {
  // app.hooks('app:render')
  app.api = axios
})
```


## types

// TODO

# Drawbacks

- `setup` maybe conflict with vite lifetime

# Alternatives

`api.addProviders` another approach

```tsx
export default defineModule({
  load(id) {
    if (id === 'app.js') {
      return {
        code: `<Provider><App /></Provider>`
      }
    }
  }
})
```

# Adoption strategy

If we implement this proposal, how will existing users adopt it? Is
this a breaking change? Can we write a codemod? Can we provide a runtime adapter library for the original API it replaces? 

# Unresolved questions

Optional, but suggested for first drafts. What parts of the design are still
TBD?