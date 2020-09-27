---
layout: post
title: Useful Vi Comands
date: '2019-01-14 07:29:03'
tags:
- vim
---

I use [vim](https://www.vim.org/) and [macVim](https://macvim-dev.github.io/macvim/) for text editing. This post has a list of useful commands that can be used for document editing.

**Removing blank lines**

`:v/./d`

**Removing lines**

`:g/string/d` &nbsp;

(deletes every line that contains string)

**Removing ^M character**

`:%s/^M//g`

(^M is entered as CTRL-V CTRL-M. In UNIX, you can escape a control character by preceeding it with a CONTROL-V)

