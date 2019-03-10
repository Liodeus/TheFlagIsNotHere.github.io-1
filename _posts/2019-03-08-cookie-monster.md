---
layout: post
title: Pragyan CTF 2019 - Cookie Monster
image: "/assets/img/2019/pragyanctf/cookiemonster/1.png"
categories: [general, pragyanctf2019]
tags: [pragyanctf2019, writeup]
twitter_text: "Write-up for Cookie Monster"
introduction: "Write-up for Cookie Monster"
description: "Write-up for Cookie Monster"
---

![](/assets/img/2019/pragyanctf/cookiemonster/1.png)

First let's take a look at the website :

http://159.89.166.12:13500

![](/assets/img/2019/pragyanctf/cookiemonster/2.png)

It's a simple website, but as the name of the challenge suggest and the content of the website I know that I have to work with cookies.

I tried a simple curl :

```bash
curl -I http://159.89.166.12:13500
```

Result :

```bash
HTTP/1.1 200 OK
Date: Fri, 08 Mar 2019 14:27:20 GMT
Server: Apache/2.4.29 (Ubuntu)
Set-Cookie: flag=bc54f4d60f1cec0f9a6cb70e13f2127a
Content-Type: text/html; charset=UTF-8

```

I get this value : flag=bc54f4d60f1cec0f9a6cb70e13f2127a. It seems to be a md5 hash let’s try to decode it :

![](/assets/img/2019/pragyanctf/cookiemonster/3.png)

The result is : pc (seems to be the beginning of pctf ?)

So I tried to send my command with the argument --cookie "flag=bc54f4d60f1cec0f9a6cb70e13f2127a" :

```bash
$ curl --cookie "flag=bc54f4d60f1cec0f9a6cb70e13f2127a" -I http://159.89.166.12:13500

HTTP/1.1 200 OK
Date: Fri, 08 Mar 2019 14:31:34 GMT
Server: Apache/2.4.29 (Ubuntu)
Set-Cookie: flag=114d6a415b3d04db792ca7c0da0c7a55
Content-Type: text/html; charset=UTF-8
```
I get another value of flag=, if I try to decode it I get “tf”. With the precedent hash the result is : pctf.

I tried my command a few times :

![](/assets/img/2019/pragyanctf/cookiemonster/4.png)

I automated with a script to get every value of the Set-Cookie :

```python
import os
from subprocess import Popen, PIPE



set_cookie=[]

send = Popen(['/usr/bin/curl', '-I', 'http://159.89.166.12:13500/'],stdout=PIPE)
first = send.stdout.read().split()
set_cookie.append(first[14].replace("flag=",""))

for i in range(0,23):
	send = Popen(['/usr/bin/curl',"-I", '--cookie',"flag="+str(set_cookie[i]), 'http://159.89.166.12:13500/'],stdout=PIPE)
	first = send.stdout.read().split()
	set_cookie.append(first[14].replace("flag=",""))
    

for result in set_cookie:
	print result
```
Result :

![](/assets/img/2019/pragyanctf/cookiemonster/5.png)

So now I have every value of Set-Cookie, I used [Crackstation](https://crackstation.net/) to decode all my hashes :

![](/assets/img/2019/pragyanctf/cookiemonster/6.png)

> The Flag : ```pctf{c0oki3s_@re_yUm_bUt_tHEy_@ls0_r3vEaL_@_l0t}```
