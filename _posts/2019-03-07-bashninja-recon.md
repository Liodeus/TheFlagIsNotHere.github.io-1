---
layout: post
title: NeverLAN CTF 2018 - BashNinja's Recon
image: "/assets/img/2018/neverlanctf2018/bashninjarecon/1.png"
categories: [general, neverlanctf2018]
tags: [neverlanctf2018, writeup]
twitter_text: "Write-up for BashNinja's Recon"
introduction: "Write-up for BashNinja's Recon"
description: "Write-up for BashNinja's Recon"
---


![](/assets/img/2018/neverlanctf2018/bashninjarecon/1.png)

First let’s search for BashNinja.

I found his website → [Link](https://www.thebash.ninja/)

At the bottom of it we have his name :

![](/assets/img/2018/neverlanctf2018/bashninjarecon/2.png)

On his personnal twitter we have the name of a school UVU :

![](/assets/img/2018/neverlanctf2018/bashninjarecon/3.png)

*UVU stands for : Utah Valley University*

Some google searching and we now have the website : [Link](https://www.uvu.edu/)

Here we have the club list : [Link](https://www.uvu.edu/clubs/clublist.html)

Let’s search for Security we found this club :

![](/assets/img/2018/neverlanctf2018/bashninjarecon/4.png)

At this link we have some members of the club : [Link](https://www.uvucsc.com/officers/)

And look what we found :

![](/assets/img/2018/neverlanctf2018/bashninjarecon/5.png)

We have the flag : f{-ustc-y-o.dlgyusol-tr–lba-orsho..-i}aohdaautuclId

*And a hint to decrypt the flag → fence*

After some reseach, I found that it was RailFence and search for an online decrypt tool :

[Link](https://www.geocachingtoolbox.com/index.php?page=railFenceCipher)

![](/assets/img/2018/neverlanctf2018/bashninjarecon/6.png)

> The flag : flag{you-should-start-a-club-at-your-school…I-did}