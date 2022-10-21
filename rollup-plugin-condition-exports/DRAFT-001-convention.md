- Start Date: 2022-10-21
- Reference Issues: (fill in existing related issues, if any)

# Summary

Supports auto convert filename exports fields pattern. Just like nextjs pages convention.

# Basic example

```console
src
  exports
    module.ts
    feature
      [...all].ts
```

will convert to 

- `/module`
- `feature/*.js`

# Motivation

According to https://nodejs.org/api/packages.html#exports-sugar, exports field support `*` in exports. also support `imports` for private module. it looks like ssr pages convention.
And not need to set rollup input fields, will automaticly lookup exports & import folder. 

# Reason
