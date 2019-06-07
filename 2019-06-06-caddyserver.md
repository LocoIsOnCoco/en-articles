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
Caddy server is a simple, yet **heavily** extensible webserver written in Go.
It has been praised by many security experts since it's open-source and has the most secure defaults built-in.
When you install caddyserver, it will download only a single binary and give it the proper permissions. By default this program will not have extensions built-in, but they can easily be added on the website.

Compared to other web servers, Caddyserver has a native automation feature to fetch free SSL certificates from Let's Encrypt, exactly like Certbot does with Nginx and Apache.

> Please note that this will not work for any domain not exposed to the clearnet, and therefore LAN IP addresses and custom DNS configurations cannot get a SSL certificate automatically.

## How does it work and what requirments does it have?
It works by making a simple webserver for displaying static content like most webservers. It can also handle PHP in pretty much the same way `nginx` does, using sockets or by reverse proxying (whilst Apache supports it natively).
It has verry little in the way of requirements, it supports all major platforms: Apple, Linux, Windows, BSD, Solaris, Plan 9, NACL and Dragonfly.
Since this program is open-source, it is really easy to modify it if you have experience in Go.

## Use cases?
Feel free to use Caddy for all possible imaginable uses that are expected from a web server, notably serving static content, testing HTML/js-based applications... except that Caddy will make you do it in a comfortable breeze, with blatant ease.

## Installation
To install Caddyserver, it is very straightforward:
```sh
curl https://getcaddy.com | bash
```
Otherwise, you can use the direct link: `https://caddyserver.com/download/windows/amd64?license=personal&telemetry=off`
These instructions are for Linux - if you need to get it for other platforms check the [official website](https://caddyserver.com).
Please note that while Caddy is open-source, it doesn't necessarily mean it's free. Caddy, on the free level, can only be used for non-commercial use, but requires paying for commercial uses. (which is the same as Nginx)
  
There are a few ways to configure Caddy beyond the defaults you get when you run the command. 
For example, persay you are trying to test a html application that needs some specifc server side settings and the files are stored at `/home/user/projects/html-app/`. 
Make a file in the application folder named `Caddyfile`, Caddy will look for this file in its current working directory, and if it exists, use that configuration. 
Or you can specify a different Caddyfile that is somewhere else on your system by using the `-conf` flag like so, `caddy -conf /home/user/caddyfiles/basic` and it will load that specific config file. I use this to keep myself from writing the same lines of code over and over and just have specific config files for each of these tasks.

Persay you want to have a universal config that you can import to save you time for example, `php`. Make the file with the php caddy config, `/home/user/caddyfiles/php` and add this to the appropriete location in your original Caddyfile `import /home/user/caddyfiles/php`

> DISCLAIMER: You must manually make these configs yourself

## Example Caddyfile. 
```
:80 {
  index index.html
  log     ./Caddylog
  errors  ./Caddyerr
}
```
---
Written by **Zachary M.M. Duncan**, corrected by **Rémy Samkocwa**
