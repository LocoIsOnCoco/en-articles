---
layout: post
title: "Caddyserver"
date: 2019-06-06
categories:
  - Webserver
  - Technical
description: A fast and easy web server
featured-img: 2019-06-06
---

# Caddy Server
## What is CaddyServer?

Caddy server is a simple, yet heavily extensible webserver written in Go. It has been praised by many security experts since it’s open-source and has the most secure defaults built-in. When you install caddyserver, it will download only a single bianry and give it the proper permissions. By default this program will not have extensions built-in, but they can easily be added on the website.

Compared to other web servers, Caddyserver has an automation feature to fetch free SSL certificates from Let’s Encrypt, exactly like Certbot does with Nginx and Apache.

> Please note that this will not work for any domain not exposed to the clearnet, and therefore LAN IP addresses and custom DNS configurations cannot get a SSL certificate automatically.

## How does it work and what requirments does it have?

It works by making a simple webserver for displaying static content like most webservers. It can also handle PHP in pretty much the same way nginx does, using sockets or by reverse proxying (whilst Apache supports it natively). It has verry little in the way of requirements, it supports all major platforms: Apple, Linux, Windows, BSD, Solaris, Plan 9, NACL and Dragonfly. Since this program is open-source, it is really easy to modify it if you have experience in Go.

## Use cases?

Feel free to use Caddy for almost all possible uses once can expect from a web server, notably serving static content, testing HTML/js-based applications. Php is also easily configurable provided you have `php-fpm` installed on the server.

##Installation
To install Caddyserver for personal use, it is very straightforward:

```sh
curl https://getcaddy.com | bash -s personal
```

    Please note that while Caddy is open-source, it doesn’t necessarily mean it's FOSS. Caddy, on the free level, can only be used for non-commercial use, but requires paying for commercial uses. For more information please go to the [Official Website](https://caddyserver.com)

There are a few ways to configure Caddy beyond the defaults you get when you run the command. 
For example, persay you are trying to test a html application that needs some specifc server side settings and the files are stored at `/home/user/projects/html-app/`. 
Make a file in the websites folder named `Caddyfile`, Caddy will look for this file in the current working directory, and if it exists, use that configuration, or you can specify a different Caddyfile that is somewhere else on your system by using the `-conf` flag like so, `caddy -conf /home/user/caddyfiles/basic` and it will load that specific config file. I use this to keep myself from writing the same lines of code over and over and just have specific config files for each of these tasks.

Perhaps you want to have a universal configuration for php that you can import to save you time, for example. Make the file with the php caddy config, `/home/user/caddyfiles/php` and add this to the appropriete location in your original Caddyfile import `/home/user/caddyfiles/php`

> DISCLAIMER: You must manually make these configurations yourself due to the infinite number of possibilities

### Example Caddyfile.

```
:80 {
  index index.html
  log     ./Caddylog
  errors  ./Caddyerr
}
```

## Cons
Now that we have discussed the pros of Caddyserver, we can talk Cons. A lot of forums and prebuilt PHP applications utilize a `.htaccess` file. Caddy does not currently support these files so you will have to rewrite this file by hand into your caddyfile. Documentation for this is available.
And unfortunately, when you run this as a service like you would a normal web server, its error log files have to be added and made by hand in the caddyfile.
And you need the plugin `hook.service` in order to easily use it as an actual service and get SSL certificates. Along with the fact that `service caddy status` and `systemctl status caddy` don't actually show what caddy is doing and instead you have to look in `journalctl -xe` to see what errors it is spewing at the time being. Usually, these errors are as simple as misplacing/forgetting to add a line somewhere in the config 

---
Written by **Zachary M.M. Duncan**, proofread and edited by **Rémy Samkocwa**
