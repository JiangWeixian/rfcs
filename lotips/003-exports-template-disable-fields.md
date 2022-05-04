- Start Date: 2022/05/01
- Reference Issues: (fill in existing related issues, if any)
- Implementation PR: (leave this empty)

# Summary

disable fileds on exports template generate, e.g.

- disable `types` will make package.types be empty
- disable `exports.[key].require` will only make `exports.[key].import` exit

# Basic example

in default, exports template geneate 

```
exports
main
module
typesVersion
types
```

- disable level-1 field `exports` 
- disable sub field `exports.require`


# Motivation

Sometimes, types filed is not auto-generated, it's manual wroten by developer.

# Detailed design

original logic still same.

disable fields after original logic, force delete `disable fields` regardless of other settings.

# Drawbacks

design all fields and subfields, looks like a little bit complex. Disable exports[key].require field not an common case.

# Alternatives

not allowed disable subfields, e.g `exports.require`

# Adoption strategy

not allowed disable, and manual overwrite by developer.

# Unresolved questions

