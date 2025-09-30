---
title: "Technologies I Used To Build This Website"
date: 2021-09-17T22:24:40+02:00
description: "A brief summary of the technologies I used to build and host my portfolio."
menu:
  sidebar:
    name: Technologies Used
    identifier: technologies
    weight: 30
hero: laptop.webP
---

In this post, I will explain the technologies that power this website. I mainly created this website to serve as an "online portfolio" to showcase my skills and projects, as well as an outlet to blog about things I am interested in such as Linux, Open Source, Web Development, and everything related to technology in general.
To create a portfolio website, you have three options, more or less. The first one is to use a traditional CMS such as Wordpress or Joomla. While this option is great for those who prefer an easy to set up solution, it might not be optimal for others that prefer minimal approaches. The second one is to create your website from scratch using HTML and CSS. This is obviously the best choice for tinkerers and those who like to customize every bit of their site. However, since this method requires a considerable amount of work and also a decent amount of programming skills, it can easily become a time-consuming black hole that can potentially hamper your productivity as maintenance costs increase over time. Finally, there exists a third option that consists in using static site generators which are trendy nowadays. This sort of acts as a middle ground between the aforementioned solutions, giving you the advantages of both worlds. After careful consideration, I opted for a static site generator to build my portfolio. 

Since I already had experience using a static site generator (Jekyll) to build a blog ([Tootips](https://www.tootips.com)), going this route was a no-brainer for me. This very article that you are now reading was created using Hugo: A static site generator written in Go. Unlike Jekyll, which is written in Ruby, Hugo is incredibly fast thanks to the power of the Go language. The only drawback though is that Hugo doesn't have a plugin system like Jekyll does. However, since I mainly intend to use it to build a portfolio site, having a plugin system isn't a must-have feature for this particular use case.

---
## Server

To host this website, I used a VPS provided by OVH. It has the following specs:

- 2 GB of RAM
- 1 vCPU
- 20 GB SSD

As you can clearly see, those specs are more than enough to host a static website.

## Deployment

Since this is a simple static website, I use Nginx to serve it. As for deployment, I run an `rsync` command to upload my `public` folder to the remote server, and to also keep my local version in sync with its remote counterpart.

In case you are curious about the `rsync` command, here is how it looks:

```
sudo rsync -aAXH --delete --quiet -e 'ssh -p <<put your ssh port here>> -i /home/yusarch/.ssh/nopw_id' \
--rsync-path="sudo rsync" ./public/ user@51.210.242.53:/var/www/html/hugo/portfolio/ \
--log-file=./rsync-hugo-portfolio.log
```
---

That's all folks! I hope this gave you a clear idea about the process and the technologies I used to build this site. See ya in my next article 😉