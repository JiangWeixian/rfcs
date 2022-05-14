- Start Date: 2022/05/14
- Reference Issues: (fill in existing related issues, if any)
- Implementation PR: (leave this empty)

# Summary

- upgrade website ui
- and more friendly integration

# Basic example

lookat https://brianlovin.com/writing/framer-sites-first-impressions

main parts of upgrade

1. sheet/id detail will not display like a card
2. mv footer into navigate
3. remove avatar
4. homepage only display recently created sheet, and remove search input box
5. replace granen with mayumi

There are some small and detail upgrades like

- menu hover effects, it related to native macos hover effects

# Motivation

Not a pro designer, https://brianlovin.com/writing/framer-sites-first-impressions is looks like better, and very suit for cheatsheet website

remove avatar, it makes website looks like app

mv footer into navigate, main part is total about cheatsheet content

sheet/id detail page not display like card, previously, the propose of display-like card is preview sheet shared image card style.

- current it dislay cheasheet content
- preview shared card style in normal sheet flow

homepage part

- some-day-i-learn part duplicated with slack bot
- searhbox now trigger by hotkey, because, most time, i use keyboard more than mouse device. hotkey make search cheatsheet much fast

# Unresolved questions

- [ ] search item is md style, cound render in dangeroushtml?