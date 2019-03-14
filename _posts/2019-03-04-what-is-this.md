---
layout: post
title: ISITDTU CTF 2018 - What is this
image: "/assets/img/2018/isitdtuctf2018/whatisthis/1.png"
categories: [general, ISITDTUCTF2018]
tags: [isitdtuctf2018, writeup]
twitter_text: "Write-up for What is this"
introduction: "Write-up for What is this"
description: "Write-up for What is this"
---

![](/assets/img/2018/isitdtuctf2018/whatisthis/1.png)

First, let’s take a look at these files :

![](/assets/img/2018/isitdtuctf2018/whatisthis/2.png)

I think this two files are the SAM and SYSTEM file.  So I unpacked them with samdump2 :

```
samdump2 -o test.txt 2 1
```
![](/assets/img/2018/isitdtuctf2018/whatisthis/3.png)

These are some windows password hashes !!! Let's try to decode them :

![](/assets/img/2018/isitdtuctf2018/whatisthis/4.png)

Using [Crackstation.net](https://crackstation.net/)

![](/assets/img/2018/isitdtuctf2018/whatisthis/5.png)

> Flag : ```r4inb0w```