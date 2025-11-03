---
title: 'Customizing Godot Mono To Use Neovim'
date: 2025-11-02T00:00:00-05:00
draft: false
author: Keith Henderson
tags: ['neovim', 'game development', 'c#', 'programming']
---

## Setting A Custom Editor
I did not really like using the built in editor that comes with Godot, so I decided to see how I could set up Neovim to launch instead. I had a few customizations and I thought I would note them down here if I ever needed to reference them again.

We need to launch nvim with our preferred terminal and give it a custom title so we can find it in hyprland.

In Godot → Editor Settings → Text Editor → External, set:

Exec Path: /usr/bin/kitty

Exec Flags: --title "GodotEditor" -e nvim +{line} {file}

## Setting Up Window Rules
I am using hyprland so I wanted it to launch on my second monitor, in a specific workspace. This required some custom window rules.

This will launch it where we require it, but it will steal focus.
```
windowrulev2 = workspace 7, monitor:1, title:^(GodotEditor)$
```

This will do the same, but it will not steal focus.
```
windowrulev2 = nofocus, workspace 7, monitor:1, title:^(GodotEditor)$
```
