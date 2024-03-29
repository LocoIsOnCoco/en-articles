---
layout: post
title: "Obtain a free domain name!"
date: 2019-02-09
categories:
  - Web
description: “Did you know that you could get a free domain to develop a website?”
featured-img: 2019-02-09
---

Thanks to GitHub education, it is possible do obtain a free '.me' domain provided by Namecheap. You can also host your website for free on GitHub if you don't have a personal server!

# Requirements

* Be currently enrolled in a **degree** or **diploma** granting **course of study**
* Have a **verifiable school-issued email address** or **documents** that prove your current **student status**
* Be **at least 13 years old**

<hr>

#### 1. Create a GitHub account

First of all, you need to visit [github.com](https://www.github.com) and create your account with your **school email address**. Once you finished filling the registration form, click the verification link in your inbox and log in on yuor account. 

> If you already have an account, just make sure that your school email address is marked as default and public in the settings

<hr>

#### 2. Join GitHub education

Now you'll need to head over to [education.github.com/discount_requests/new](https://education.github.com/discount_requests/new) and enter all details asked. Make sure to select the correct **school-issued email address** and **school name**. Once you have received your **student pack**, you may continue with the last step!

<hr>

#### 3. Get your free domain name

Finally, visit [nc.me](https://nc.me/) and search for an available **.me** domain. Add it to your cart and complete the order. Make sure to enter your **school email** address as it's your **primary email** on GitHub!

* If you're planning on hosting your website with GitHub, select **GitHub pages** and follow this tutorial: [https://gist.github.com/lukalafaye/b9733a2d45b1e50e58a0f3ac91a77503](https://gist.github.com/lukalafaye/b9733a2d45b1e50e58a0f3ac91a77503)

* If you're planning on hosting your website on a personal server, select **Ghost Machine, Managed by Namecheap**

<hr>

Once you've finished creating your account, log in on [namecheap.com](https://www.namecheap.com/). Click your username and move to your **dashboard**. In the nameservers section, select **Namecheap BasicDNS** and apply by clicking the green tick mark.

Move to **Advanced DNS** in the top menu and add a new record. Fill with:

| TYPE          | HOST  | VALUE         | TTL       |
|-------------- |------ |-----------    |--------   |
| A record      | @     | 0.0.0.0       | 30 min    |

<br>

Where 0.0.0.0 is your server's or GitHub's **IPv4 address**. You can get your server's IP it by executing curl:

```bash
curl -s checkip.dyndns.org | sed -e 's/.*Current IP Address: //' -e 's/<.*$//'
```

<br>

GitHub's IP should be `204.232.175.78`, check the tutorial for more information.


---
Published by **Luka Lafaye de Micheaux**
