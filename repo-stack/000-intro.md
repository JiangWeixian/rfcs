- Start Date: 2022/04/03
- Reference Issues: https://github.com/JiangWeixian/rfcs/issues/15
- Implementation PR: (leave this empty)

# Summary

List all npm packages contain used in project.

# Basic example

Publish it as web ext app. 

1. Enter github.com/user/repo
2. Read package.json file and list all npm packages listed.

# Motivation

When i read pkg source code, I just want to know what the npm do, there are some steps:

1. Open repo github page
2. Copy npm package name
3. And search on google

Will be much better if I can list they all once-time.

## Tech Stack

1. https://github.com/saadeghi/daisyui
2. vite

## Usage

1. Click ext icon, and list all npm readme in float panel

# Unresolved questions

- [ ] Select text and popup, display readme content in popup element.