- Start Date: 2022/02/03 20:20:06
- Reference Issues: (fill in existing related issues, if any)
- Implementation PR: (leave this empty)

# Summary

without write reducers, `use-rematch` export api like `chain-api` or `built-in` useful reducers to help developers quick modify react-redux state.

# Basic example

```ts
const { dispatch, chain } = useRematch({ num: 1 })

dispatch.update(partialState) // partial update state
dispatch.set(nextState) // overwrite total state

chain(state => partialState)
  .add(1)

chain(state => partialState)
  .insert(index, element)
```

# Motivation

now rematch reducer have to define like

```ts
const { dispatch, chain } = useRematch({
  state: { num: 1 },
  reducers: {
    update: (state, partialState) => {
      return { ...state, ...partialState }
    },
    set: (state, nextState) => {
      return nextState
    },
  }
})
```

but `useState` in default provide `setState` api. it make `useState` much simple.

# Detailed design

**feature-1: built-in update & set reducer**

```ts
check(model.reducers contain update or set) if exits throw warnings
finialReducers = merge(model.reducers, builtIn.reducers)
```

**feature-2: chain-api**

```ts
{
  state, // promise state
  chain() {
    state = promise(partial state callback)
    return this
  },
  add() {
    // modify state
    state = then(modified state)
    return this
  },
  end() {
    // update state by this.state
  }
}
```

- [ ] **how make state in chain partial update**

# Drawbacks

**feature-1**

built-in `set & update` reducers

- not increase lib size
- is breaking change

**feature-2**

if `chain` is built-in feature

- heavy increase lib size
- not a breaking change

# Alternatives

provide reducers exported from pkg

```ts
import { reducers } from '@use-rematch/core'

const { dispatch, chain } = useRematch({
  state: { num: 1 },
  reducers
})
```

# Adoption strategy

- warning in dev, if user's model-reducers contain `set or update` action

# Unresolved questions

- [ ] - should we builtin chain in default, or make `plugin-chain`