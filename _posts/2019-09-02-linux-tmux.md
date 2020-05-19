---
layout: post
title:  "How to: tmux"
date:   2019-09-02 09:43:04 -0500
categories: linux
permalink: /linux/tmux
---


## create new session
`tmux`
## create new session with name
`tmux new -s <sessionName>`

## to split right and left panes - focus is on right pane
`ctrl-b` then  `%`

## to split top and bottom panes - focus is on bottom pane
`ctrl-b` then `"`

## to switch to left pane
`crtl-b` then `<arrow key>`

## to exit pane
`crtl-d`
or
`exit`

## to open new screen
`crtl-b` then `c`

## to switch between screens - previous
`crtl-b` then `p`

## to swtich between screens - next
`crtl-b` then `n`


## to detach session
`ctrl-b` then `d`

## to list detach session
`tmux ls`

## to attach session again - the first character of tmux ls input
`tmux attach -t 0`

## to attach name session again.
`tmux attach -t`
