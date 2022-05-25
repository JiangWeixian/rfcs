- Start Date: 2022/05/24
- Reference Issues: (fill in existing related issues, if any)
- Implementation PR: (leave this empty)

# Summary

Build personal blog site.

- self host domain(not a vercel domain or netlify domain)

# Basic example

website should like <jwx.ink>, domain should be as short as possible.

- <jwx.me>
- <jwx.ink>

# Motivation

1. You should always keep share you learn, think, create, reading, workspace etc... The more you share, the more you learn.
2. Improve seo - your impact on community bring money and let your creating know to others
3. Social - you will find your Friends based on your shared content.

# Detailed design

Features in brief

- Website should be **fast**
- Simple, not group by tags is ok in first version.
- Searchable is not required 

Milestones

- [ ] blogs like website + dark style(no light mode)
- [ ] Self Introduction, like https://evanyou.me/
- [ ] RSS/mail subscribe, blog update/products update. currently is blog update
- [ ] homepage(or another specific tab) build with threejs
- [ ] link to your products(products may has own website), list your products(on this personal blog website)
- [ ] Resume
- [ ] Blog comments system

## Tech stacks

- (framework) nextjs
- (style) tailwindcss + mayumi(dark only)
- mdx, cound enhanced basic markdown grammar with custom ;components
- (fast speed) static website

https://github.com/leerob/on-demand-isr/blob/main/pages/index.tsx;

ISR, awesome nextjs feature

1. issue to static website
2. auto revalidate and generate new website without deploy

### UI

Mayumi, tailwindcss, dark theme

- Mayumi provide default components/layout and theme
- tailwindcss typography render markdown content

## Blog

`/issues` - blog issues list

layout, simple issue lists

`/issues/[id]` - issue detail content

- main part, blog content
- create at
- tags? issue category.
- next and prev issue link

### CRUD

Edit/Create Blog content has hight frequent updates, should be as simple as possible. others like resume etc... has less frequent updates.

~~never push blog content in website~~

1. create blog article in github issue
2. render github issue into page

# Unresolved questions
