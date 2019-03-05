---
layout: post
title: Timisoara CTF 2018 - Neurosurgery
image: "/assets/img/2018/timisoaractf2018/neurosurgery/1.png"
categories: [general, timisoaractf2018]
tags: [timisoaractf2018, writeup]
twitter_text: "Write-up for Neurosurgery"
introduction: "Write-up for Neurosurgery"
description: "Write-up for Neurosurgery"
---


![](/assets/img/2018/timisoaractf2018/neurosurgery/1.png)

So we are given a zip containing a large file name image (2,1G). Look like a memory dump. Let’s find out with volatility what kind of dump we have.

![](/assets/img/2018/timisoaractf2018/neurosurgery/2.png)

So this is not a windows dump. Linux maybe ?

![](/assets/img/2018/timisoaractf2018/neurosurgery/3.png)

Linux it is ! So now we need a profil to work with volatility on it. Let’s make it.

First I downloaded an Ubuntu version 16.04.4 [Link](https://www.ubuntu.com/download/desktop), then run virtualbox with this iso, install it and use these commands :


```
apt-get install dwarfdump build-essential linux-headers-4.4.0-116-generic volatility zip
cd /usr/share/volatility/tools/linux/
make
zip /home/Profil.zip ./module.dwarf /boot/System.map-4.4.0-116-generic
```

After that you take the zip file and place it here : /usr/lib/python2.7/dist-packages/volatility/plugins/overlays/linux/

Your profil is now ready ! First I want to see if there was some commands left.

![](/assets/img/2018/timisoaractf2018/neurosurgery/4.png)

And there is ! So as you can see there is something weird going on with ht0p, why not dump it to see what it does ?

![](/assets/img/2018/timisoaractf2018/neurosurgery/5.png)

![](/assets/img/2018/timisoaractf2018/neurosurgery/6.png)

![](/assets/img/2018/timisoaractf2018/neurosurgery/7.png)

> And there you have the flag : timctf{ch4nc3_f4vors_th3_pr3p4red_m1nd}