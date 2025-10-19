---
title: "Moving Sucks... Rust Doesn't?"
date: 2025-10-19T00:00:00-04:00
draft: false
author: Keith Henderson
tags: ['rust', 'arch', 'programming', 'life']
---

## Moving Sucks

We recently sold our home and were tasked with finding a new one. Without going into detail the entire experience was less than desirable. The dust has finally settled and life has returned to some normalcy. We have not moved houses yet, but the houses are bought and sold, and I would say that is the worst part of the entire thing. Now that it is over I have been able to relax a bit and focus on some of the things I enjoy.

## Learning Rust

I recently started looking into learning Rust. So far it has been a pretty good experience and I am enjoying it. I am realizing the capability of the language and that makes me really excited. I have dabbled in a lot of different languages but I always seem to get hung up on what it can and cannot do. All languages have their strengths of course but from what I have learned so far it seems that Rust can do a lot of different things really well (at least stuff that interests me). It's also new and has great documentation like the Rust book. It is really incredible the entire thing is online. You can find a copy of it [here](https://doc.rust-lang.org/book). I am still learning a lot but so far it is pretty cool.

## Applied Knowledge

One problem I always seem to face when learning languages is spending a ton of time learning and then I am not sure what to create with it. A while ago I had purchased a wireless headset and at the time I did not realize the dongle did not have the Chatmix volume knob inline. This proved to be an issue on Linux as the drivers to control it were of course proprietary and not available on Linux. Initially I found a solution that was written in Python and after forking and modifying it, it seemed to work pretty well. As someone who was learning Rust, there was only one thing I could...

## Rewrite it in Rust

As is tradition I had to take something that was not technically broken and rewrite it in Rust. This actually turned out to be pretty good and work extremely well. I was able to remedy some of the issues with the Python version and also tailor a few more things to my liking. I will admit I did rely heavily on co-pilot to guide me through writing it as I am still relatively new to Rust, but overall it was a great experience to see *how* something could work like this in Rust. I was able to create an install script which implements a persistent Systemd service that will wait through disconnection and it *just works*. The Chatmix dial functions just as well as it would with the proprietary drivers and so far I have no had any issues.

## Moving Forward

I am excited to continue to learn more about Rust and work my way through the book. Working with hardware and debugging with Rust was a cool experience that I have never really done before (outside the Python fork of the original solution).

Cheers,

Keith

Below is a link to the Arctis Nova 7 Wireless Chatmix userspace daemon on Github:
{{< github user="lairizzle" repo="arctis-nova-7-wireless-chatmix" >}}
