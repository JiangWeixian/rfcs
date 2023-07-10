- Start Date: 2023/05/21
- Reference Issues: (fill in existing related issues, if any)
- Implementation PR: (leave this empty)

# Summary

Like [runjs.app](https://runjs.app/), but implement via vite version. It's another kind of repl.it application.

# Basic example

1. Install via npm packages
2. Boost via `vit ...` (maybe has other sub commands), will open new browser tab in localhost server.
3. Write some codes, send code to backend server (maybe trigger via `ctrl-s` keyboard).
   - Support import remote package like esm.sh
4. Run code in backend, pipe node console[...method] `(maybe only log method)`

# Motivation

- I always need test how to use a third package via some demo code.
  1. Method 1 - use offical npm repl.it page -  **very slow**
  2. Method 2 - use download npm to local side, run it via `esno`. - Maybe the best way yet, but need clear project files after some times(maybe two weeks or months.)
  3. Method 3 - runjs.app. **Two arge application.**

# Detailed design

- Backend via `vite`
- built-in code editor page.
- Support import remote package via remote package url (like esm.sh). Remote package should be cached for the further use.
- New page via subcommand and client-side operations.
- Should support preview client-side apps and server-side apps?

*There are lots of todo, lack of demo codes*

# Drawbacks

It's not an towards to users(not developers) production. Still towards developers. Which means hard to gain moneys

# Alternatives

Write demo code just like these days...

# Unresolved questions


- [ ] Demo code
- [ ] Is strong demand?