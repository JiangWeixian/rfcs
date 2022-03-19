- Start Date: 2022/03/19
- Reference Issues: https://github.com/JiangWeixian/lotips/issues/44
- Implementation PR: (leave this empty)

# Summary

limit formats options.

# Basic example

formats allow `cjs,esm,es`, normalize into `cjs,es`

so other options also allowed `esm,es`, have to further job to normalize `esm` -> es

# Motivation

```ts
{
  esm: string
  cjs: string
}

// but formats is

[cjs, es]
```

# Alternatives

- normalize `esm,es` in all options key.

button `esm,es` all in dirs option, it looks like very confused.