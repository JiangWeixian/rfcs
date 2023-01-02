- Start Date: 2022/12/16
- Reference Issues: (fill in existing related issues, if any)
- Implementation PR: (leave this empty)

# Summary

A serverless component app. Each endpoint will render a component.

# Basic example

- `mdx.svg` - receive remote `md` url, and render it in tailwindcss typography styles.
- `webgradients.svg` - render prettier webgradients background.

etc...

# Motivation

Inspired by `rsc` and `svg.foreignObject` support render html elements inside svg. Feel like kinds of `rsc(react-server-components)` which support render in server side, client will receive servalized result, and render in client side. 

I want to these realme (remote) components help user build prettier style hero image and readme.

# Detailed design

I want to design this website into two parts:

1. some out-of-box endpoint(components) with great styles, style these components with url query. take url query as props.
2. some basic components to support user write custom component with those `out-of-box(components)`
3. a react library like `realme/svg` & `realme/img`. `realme/svg` receive props as state and then render svg element(support css events) into website; `realme/img` render into image.

## out-of-box components

## reuseable

## realme/svg and realme/img


# Drawbacks

A litter complex usage when write custom wiget(or named components). The reason is that hard to write with css. Built in components with great design would much better.

# Unresolved questions

- [ ] how to design basic components, easy to combine.