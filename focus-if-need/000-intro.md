- Start Date: 2023/05/13
- Reference Issues: (fill in existing related issues, if any)
- Implementation PR: (leave this empty)

# Summary

Automatic focus element if element is avaliable. 

# Basic example

```ts
import { focusIfNeed, history } from 'focus-if-need'

// input is element ref, automatic focus element if it mouted
focusIfNeed(input) 

// history
history.stacks
history.length
history.listen

// create own focus-if-need managed
createFocusIfNeed()
```

# Motivation

When I deploy `#aiflow`, I meet an issue:

```tsx
<panel>
  <input ref={ref}>
</panel>
```

I auto focus input ref when panel mounted in `useEffect` hooks. However currently `<input />` is not mouted yet. Or it's controlled by state e.g. `visiable`. There are two ways to implement it:

1. Wrap `<input />` into react-component `<Input />`, focus when mouted
2. Sometimes, third party components will provide a ref for us, we can check ref is already exsits in `setInterval`. And automatic focus if ref is ready to use.  

**In additions:**

```tsx
<panel>
  <input ref={ref}>
</panel>
<modal />
```

When close modal, I want to focus panel.input automatic. `focus-if-need` will provide a mananger to control which input should be focus.

# Detailed design

`focus-if-need`

```tsx
// global hooks:
// map id to element ref
const hooks = {}

const focusIfNeed = (ref) => {
  // interval check ref is avaliable
  ref.focus()
  // register
  hooks.register(ref)
  // history
  history.push(ref)
}

// history
// record focused element
history.stacks
// callback if active element change
history.listen
```

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