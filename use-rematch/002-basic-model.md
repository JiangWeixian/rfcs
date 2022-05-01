- Start Date: 2022/05/01
- Reference Issues: (fill in existing related issues, if any)
- Implementation PR: (leave this empty)

# Summary

Built in simple model like with `set & update` reducer.

# Basic example

```ts
import { useBasic } from '@use-rematch/use'

const { dispatch } = useBasic()

dispatch.update()
```

- `update` partial update model
- `set` replace original model state

Behavior like reducer version `useState`

# Motivation

create model with `useReducer` is so much different.

# Detailed design

basic is created by original useReducer, but built in `set & update` reducer.