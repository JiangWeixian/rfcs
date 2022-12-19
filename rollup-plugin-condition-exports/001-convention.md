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

# Detailed design

## Rules

1. All files under `exports` should be exported, no much more `exclude` patterns by default. real `api` should write into other folders like `node` or `client`
2. extensions should be `tsx ts js jsx` by default
3. `./package.json` will auto setup in exports fields

## Cases

### main & module fields

`main` and `module` fields

```console
src
  exports
    index.ts
```

`exports/index.ts` will setup `main & module` field in `package.json`.

### condition names

by default, preserved `node & browser & deno & default` condition, e.g. 

```console
src
  exports
    config
      node.ts
      browser.ts
      deno.ts
```

will convert into

```json
{
  "exports": {
    "config": {
      "node": "...",
      "browser": "...",
      "deno": "...",
    }
  }
}
```

will auto generate both `require & import` fields

```
config
  leaf: false
  children
    - node
      leaf: true
```

*custom condition like should support in args.*

### disable on subpath

```console
src
  exports
    config
      node.ts
      browser.ts
      deno.ts
    config.ts
```

will convert into

```json
{
  "exports": {
    "config": "",
    "config/node": "",
    "config/browser" : "",
  }
}
```

internal state

```yaml
config
  leaf: true
  children
    - node
      leaf: true
```

## require or import only

by default `node.ts` will both `require & import` fields. If filename include `.cjs.ts` extensions, will only generate `require` field.
