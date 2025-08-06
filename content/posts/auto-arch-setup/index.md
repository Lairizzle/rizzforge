---
title: 'Auto Arch Setup'
date: 2025-06-20T21:38:02-04:00
draft: false
author: Keith Henderson 
tags: ['computers', 'arch', 'automation', 'bash']
---

## Automating My Post Install Experience
It is always nice booting into a fresh system. The only problem is getting everything setup the way you like after the install is done. Since switching to Linux as my daily driver over a year ago, I have learned a lot in regards to setting up and configuring my system. If you are new to linux you may have heard the term 'dot' files. If you are not sure what that means, they are referring to your configuartion files. Typically applications will store configs like themes in your .config folder in the home directory, hence the name 'dot' files. This is only part of automating your post install setup, but it is a pretty big one.

## Dot, dot, dot

If you have not already made a github/gitlab repository for all of your dot files, then why are you still reading this? This has been tremendous time saver for me personally. Most dot files can be made public, so you can easily clone or share them - just make sure they don't include any sort of sensitive information. For example, I have a repo called [GruvDots](https://github.com/Lairizzle/GruvDots) which contains dot files for a Gruvbox themed hyprland setup I use. When I created this repo, I added my git init right inside my .config folder, then I created a .gitignore file that looks like this:

```
# Ignore everything in repository root 
/*

# Files to not ignore
!/.gitignore
!/some_other_files

# Folder to not ignore
!/btop/
!/dunst/
!/hypr/
!/kitty/
!/mc/
!/lazynvim/
!/nvim/
!/rofi/
!/wallpapers/
!/waybar/
```
So what is this doing? This .gitignore will ignore everything in my .config folder, but then it will not ignore the folders I specify. This allows me to easily decide which configs get pushed to my repo.

## Automating with Bash
Bash scripting is amazing. It is so much fun to create useful bash scripts to help automate things and a post install setup is no exception. When dropping into a fresh Arch install on hyprland, it is pretty bare bones. With a quick install of git, I can leverage [this script](https://github.com/Lairizzle/bashScripts/blob/master/setup.sh) to automate my install.

<ol>
    <li>It sets my user name for greetd</li>
    <li>It installs a list of packages I know I will</li>
    <li>It installs yay so I can leverage the AUR</li>
    <li>It automatically installs a Gruvbox skin for Midnight Commander</li>
    <li>It clones all of my GruvDots from github into my .config folder</li>
    <li>It configures my greetd to use tuigreet and themes it</li>
    <li>It disables sddm and enabled greetd</li>
    <li>It tells me that setup is complete and then asks if I would like to reboot</li>
</ol>

This all runs within a matter of minutes and my system is setup exactly how I like it. Instantly I am able to start working on whatever I need to.

## Home Servers
The final piece that really pulls it all together is a home server or some sort of storage like NextCloud. If you have something like this set up then you can keep all of your important stuff you want to save and retain stored on your server and your home pc almost acts like a dummy terminal. If it can't be a repo on github or saved to your home server then it is basically just installed applications like games and other things you interact with, not actual data. It almost turns your computer itself into a dummy terminal, well it feels like it anyway.

Cheers,
Keith





