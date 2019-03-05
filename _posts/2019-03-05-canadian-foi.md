---
layout: post
title: P.W.N. CTF 2018 - Canadian FOI
image: "/assets/img/2018/pwnctf2018/canadianfoi/1.png"
categories: [general, pwnctf2018]
tags: [pwnctf2018, writeup]
twitter_text: "Write-up for Canadian FOI"
introduction: "Write-up for Canadian FOI"
description: "Write-up for Canadian FOI"
---


![](/assets/img/2018/pwnctf2018/canadianfoi/1.png)

This is a simple web site with two pages, index.html and about.html

![](/assets/img/2018/pwnctf2018/canadianfoi/2.png)


After some test I found that there is 300 pdf.
On the index.html page we can see a link, which redirects to [Link](http://foi.uni.hctf.fun/docs/document_001.pdf)

![](/assets/img/2018/pwnctf2018/canadianfoi/3.png)

We will try to change the number 1 of the pdf in the url by the number to see if we have access to other pdf of the site

![](/assets/img/2018/pwnctf2018/canadianfoi/4.png)


I used wget to download them all.

![](/assets/img/2018/pwnctf2018/canadianfoi/5.png)

Once we download all the pdf, we can see that one is different (number 255), it's red instead of blue.

![](/assets/img/2018/pwnctf2018/canadianfoi/6.png)

We just have to open it to get the flag.

![](/assets/img/2018/pwnctf2018/canadianfoi/7.png)

> Flag : flag{F1rst_Gr4d3rs_4r1thm3t1c_1s_d4ng3r0us}