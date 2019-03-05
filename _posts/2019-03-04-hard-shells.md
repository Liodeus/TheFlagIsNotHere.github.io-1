---
layout: post
title: IceCTF 2018 - Hard Shells
image: "/assets/img/2018/icectf2018/hardshells/1.png"
categories: [general, IceCTF2018]
tags: [icectf2018, writeup]
twitter_text: "Write-up for Hard Shells"
introduction: "Write-up for Hard Shells"
description: "Write-up for Hard Shells"
---

![](/assets/img/2018/icectf2018/hardshells/1.png)

First, let’s take a look at the file :

![](/assets/img/2018/icectf2018/hardshells/2.png)

It's a Zip archive, so try to unzip it :

![](/assets/img/2018/icectf2018/hardshells/3.png)

We need a password, I used john to crack it :

```
zip2john hardshells > hash
john hash
```

And we got the password :

![](/assets/img/2018/icectf2018/hardshells/4.png)

Now we have a Minix file whose name "d", mount it :


```
mount -t minix d /mnt/test
```

And we have a new file "dat", if we look at the header with hexdump we suppose it's a .PNG but the header has been modified :

![](/assets/img/2018/icectf2018/hardshells/5.png)

Use a hexeditor to modified the U(55 in hex) to N(4e in hex)

![](/assets/img/2018/icectf2018/hardshells/6.png)

Now you can open it and read the flag :

![](/assets/img/2018/icectf2018/hardshells/7.png)

> Flag : IceCTF{look_away_i_am_hacking}