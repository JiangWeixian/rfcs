- Start Date: 2022/02/04 11:11:22
- Reference Issues: (fill in existing related issues, if any)
- Implementation PR: (leave this empty)

# Summary

mayumi ui framework tech arch

- react
- styled-components
- tailwindcss - `tw.marco` combine tailwindcss and styled-components

rename `granen` to `mayumi`.

# Basic example

```ts
import { Button } from 'granen'
```

1. No more extra style import
2. Condition exports
3. Tailwindcss
4. macos style like

# Motivation

**tech-stack**

granen now use follow css tech stacks

- windicss(tailwindcss)
- styled-components

**windicss(tailwindcss)** make follow codes

```ts
const element = styled.div`
  @apply bg-fixed bg-blue;
`
```

translate to 

```css
{
  background-attachment: fixed;
  background-color: blue;
}
```

it heavy rely on `babel-plugin*` and `regex`, so it will not always work great~ And `tw.marco` much great.

**implement**

`mayumi` should based on open-source ui framework, in `granen`, maybe not do too much react ui implement, and lack of macos design figma resource. So switch and change variable nam, and bugs fixed too much times.

- nextui
- https://design.wonderflow.ai/

**rename**

`granen` is already `0.5.0`, but still in very `beta` mode. It make users really confused. Restart the game from `mayumi`, release version with snapshot, or link local.

**less is more**

`granen` has too much components, but not-one is perfect. So the new repo, should start from `cheatsheets`. choose less

**build docs runtime**

- better docs reference

# Detailed design

// TODO

# Drawbacks

not contain too-much components like `react-highlight`, it should outside of `mayumi`.

# Adoption strategy

- deprecated granen
- replace granen to mayumi

# Unresolved questions

- [ ] hooks of animation effects
