---
layout: post
title: SecurityFest CTF 2018 - The Oracle
image: "/assets/img/2018/securityfestctf2018/theoracle/1.png"
categories: [general, securityfestctf2018]
tags: [securityfestctf2018, writeup]
twitter_text: "Write-up for The Oracle"
introduction: "Write-up for The Oracle"
description: "Write-up for The Oracle"
---

![](/assets/img/2018/securityfestctf2018/theoracle/1.png)

Let’s have a look at this note :

![](/assets/img/2018/securityfestctf2018/theoracle/2.png)

We have a gibberish note !

My first thought was to use xortool :

```
xortool -b emsg.txt
```
Go to the result folder, and search for the flag :

```
strings *|grep sctf{
```
![](/assets/img/2018/securityfestctf2018/theoracle/3.png)

That it we got it !

> Flag : sctf{W1ll_U_571ll_du_4ll_0f_7h1s_1f_1_h4d_n07_s41d_4ny7h1ng?}