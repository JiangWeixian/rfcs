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
- gulp

**gulp**

gulp is great, but is not good in watch mode. And `es/cjs` support.

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

- [nextui](https://nextui.org/docs/theme/default-theme)
- [wanda](https://design.wonderflow.ai/)

**rename**

`granen` is already `0.5.0`, but still in very `beta` mode. It make users really confused. Restart the game from `mayumi`, release version with snapshot, or link local.

**less is more**

`granen` has too much components, but not-one is perfect. So the new repo, should start from `cheatsheets`. choose less. In `mayumi` you should make every component better and better.

**build docs runtime**

- docs references in local, too less feedback to moveon


# Detailed design

### exports

require `node>=12.20.x` and conditions exports

### color/theme system

<https://tailwindcss.com/docs/customizing-colors>
<https://coolors.co/111013-e8dab2-4f6d7a-c0d6df-eaeaea>
<https://design.wonderflow.ai/design/themes>
<https://colorable.jxnblk.com/dcdcdc/111013>

- dark mode
- light mode

define color variables

- named color like `primary|success`
- and color palette syntax like `dark-(0|1)`

### css framework

- <https://stitches.dev/>
- tailwindcss padding&width variable define

Stitches provide some utils for styled-components. Just like `vanilla-extract`.

### mvp components

- button
- input
- dropdown
- typography
- layout
- divider
- avatar
- box
- description
- menu

### docs

- https://github.com/facebook/docusaurus
  - support algolia
- live editor

# Drawbacks

not contain too-much components like `react-highlight`, it should outside of `mayumi`.

# Adoption strategy

- deprecated granen
- replace granen to mayumi

# Unresolved questions

- [ ] hooks of animation effects
