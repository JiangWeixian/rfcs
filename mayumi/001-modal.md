- Start Date: (fill me in with today's date, YYYY-MM-DD)
- Reference Issues: (fill in existing related issues, if any)
- Implementation PR: (leave this empty)

# Summary

common modal component, include follow feats

1. hotkeys <kbd>commnd+k</kbd> + <kbd>esc</kbd>
2. ui should lookat raycast

# Basic example

```tsx
<Modal />
```

`modal` contain follow components(also listed in props)

- modal mask
- modal title
- modal close icon
- hot keys <kbd>command + k</kbd> will open modal, <kbd>esc</kbd> will close modal.

`modal` support follow props

- blur
- control visible
- center modal or not
- config display close icon or not

`modal` animation is scale animation from `0.8` to `1'`

# Motivation

cheatsheets need search in modal

# Detailed design

`animation`, controled by react-spring, toggle by modal visble

```tsx
<modal-body />
<modal-mask />
```

`modal-mask` also need same animation like modal-body, it make modal animation looks like more real.

# Drawbacks

modal element design not like current morden modal element.

```tsx
<modal>
  <modal-body>
  <modal-mask>
</modal>
```

It config modal element by props. `component-structure-slot` or `component-props-slot` which one is better? I have no idea.

# Unresolved questions

- [ ] modify modal footer
- [ ] support modal animation slide from top to center
- [ ] if modal contain input element, 