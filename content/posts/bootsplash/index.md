---
title: 'Making a Custom Bootsplash'
date: 2025-09-09T00:00:00-04:00
draft: false
author: Keith Henderson
tags: ['Programming', 'C', 'Arch', 'Linux', 'Themes']
---

## A Boring Boot

I had become so content with my recent Tokyo Night theme and setup on my hyprland installation that I had started to forget how fun tinkering is. I just needed a quick fix, but I was not sure what I was missing. My current setup does everything perfectly well and fits my workflow. Then it dawned on me. I had grown tired of my boring boot. So I decided I would replace all the Systemd garbage outputs with something a little cooler.

## Making it Executable

For my greeter, I use TuiGreet which is another version of greetd. I needed my splash screen to launch before TuiGreet. I decided the splash would display some ASCII text with my main computers hostname (which is Chronos), but technically this could be set to display anything and the only the rows need be adjusted. The bootsplash was written in C and it turned out pretty good.

## Order of Operations

To get this to run at the right time I had to create a Systemd service for it. I compiled the program and moved it to /usr/local/bin and set up the service as such:

```bash
[Unit]
Description=Chronos ASCII Splash
DefaultDependencies=no
Before=greetd.service
Conflicts=getty@tty1.service
After=systemd-vconsole-setup.service

[Service]
Type=oneshot
ExecStart=/usr/local/bin/chronos
StandardInput=tty
StandardOutput=tty
TTYPath=/dev/tty1
RemainAfterExit=yes

[Install]
WantedBy=multi-user.target
```

This worked for me but of course to do something similar you would have to ensure to change the settings to work with whatever tty you are launching greetd on, If you are using greetd that is. This is not a tutorial though, just sharing something that I thought was cool.

See the gif below:

![Chronos Bootsplash](chronos.gif)


Below is a link to BootSplash on Github:
{{< github user="lairizzle" repo="bootsplash" >}}

Cheers,
Keith
