---
title: 'SDDM Trouble'
date: 2025-07-03T00:00:00-04:00
draft: false
author: Keith Henderson 
tags: ['computers', 'arch', 'themes', 'sddm', 'greeter']
---

## Monitor Issues
After changing all my theme stuff over to Tokyo Night, I wanted to spice up my greeter with a nice SDDM theme. I found a fantastic one for Tokyo Night on github by siddrs, which you can find a link to [here](https://github.com/siddrs/tokyo-night-sddm). The theme worked perfectly with the Arch install method from the AUR but there was one issue. SDDM will sometimes have a weird behaviour where it will launch across multiple monitors, but the input will default to the last monitor rendered. In my case this was my right most monitor, which is not my main monitor.

Many of the suggestions or fixes online included using xrandr to define some rules in the Xsetup file for SDDM, but none of these options ever seemed to have any effect and it was driving me crazy.

## The Fix
So how did I ultimately fix it and get it to display on my primary display? I had to make an X11 config file and place it in /etc/X11/xorg.conf.d/ 

```
sudo nvim /etc/X11/xorg.conf.d/10-monitor.conf
```

After creating this conf file I used the following config and it worked perfectly.

```
Section "Monitor"
    Identifier "DP-1"
    Option "Primary" "true"
EndSection

Section "Monitor"
    Identifier "DP-2"
    Option "RightOf" "DP-1"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device "Card0"
    Monitor "DP-1"
    DefaultDepth 24
    SubSection "Display"
        Depth 24
        Modes "1920x1080"
    EndSubSection
EndSection

```
This worked great for a two monitor display where both are 1920x1080. If you were to use this you would need to adjust the size and identifiers to be applicable to your hardware. In my case they are DP-1 and DP-2.

I wanted to make this post so that I have a reference for this fix if I ever need it again in the future.

Cheers,
Keith






