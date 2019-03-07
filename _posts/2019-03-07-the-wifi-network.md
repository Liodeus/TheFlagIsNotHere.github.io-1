---
layout: post
title: NeverLAN CTF 2018 - The WIFI Network
image: "/assets/img/2018/neverlanctf2018/thewifinetwork/1.png"
categories: [general, neverlanctf2018]
tags: [neverlanctf2018, writeup]
twitter_text: "Write-up for The WIFI Network"
introduction: "Write-up for The WIFI Network"
description: "Write-up for The WIFI Network"
---

# The WIFI Network

![](/assets/img/2018/neverlanctf2018/thewifinetwork/1.png)

So we have a WPA2 Handshake let’s crack it using aircrack-ng :

Command :

```
aircrack-ng neverlan.cap -w ./rockyou.txt
```

That’s it you have the flag !


![](/assets/img/2018/neverlanctf2018/thewifinetwork/2.png)

> The Flag: obiwan17