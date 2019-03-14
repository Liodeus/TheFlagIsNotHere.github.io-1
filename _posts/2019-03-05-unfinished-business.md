---
layout: post
title: Pragyan CTF 2018 - Unfinished business
image: "/assets/img/2018/pragyanctf2018/unfinishedbusiness/1.png"
categories: [general, pragyanctf2018]
tags: [pragyanctf2018, writeup]
twitter_text: "Write-up for Unfinished business"
introduction: "Write-up for Unfinished business"
description: "Write-up for Unfinished business"
---


![](/assets/img/2018/pragyanctf2018/unfinishedbusiness/1.png)

Open the link and you got this :

![](/assets/img/2018/pragyanctf2018/unfinishedbusiness/2.png)

Connect with your credentials and you get redirect on this page (/unavailable.php).

![](/assets/img/2018/pragyanctf2018/unfinishedbusiness/3.png)

Let’s try to connect via curl and see what happened :


![](/assets/img/2018/pragyanctf2018/unfinishedbusiness/4.png)

As you can see the location is /admin.php but we are redirect on /unavailable.php. Let’s try to go on /admin.php with curl using our PHPSESSID to stay connected.

![](/assets/img/2018/pragyanctf2018/unfinishedbusiness/5.png)

> The Flag : ```pctf{y0u=Sh0Uldn’1/h4v3*s33n,1his. : )}```