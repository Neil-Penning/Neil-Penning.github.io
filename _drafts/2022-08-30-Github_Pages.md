---
layout: post
title:  "Github Pages"
date:   2022-08-30
permalink: /:categories/:year/W:week/:short_day/:title:output_ext
categories: Project
---
# Setup
## Installing Jekyll
### On Argentum
Installing Jekyll on Argentum, my Fedora 35 server, was fairly painless.
```
dnf install ruby-devel
```
I did have to add Ruby Gems to `$PATH`
Also, I had to run `bundle add webrick` to add webrick.

### On Helium
On my 2020 M1 Macbook Air, I followed [this guide](https://jekyllrb.com/docs/installation/macos/).


## Plugins
I typically err on the side of vanilla when it comes to development environments,
    so I haven't installed the script yet.
## Jekyll-Relative-Links
### Youtube
I want to embed youtube videos in some blog posts, namely for my [[Heart]] post.
I found [this stack overflow post](https://stackoverflow.com/questions/10529859/how-to-include-video-in-jekyll-markdown-blog) which includes [this github gist](https://gist.github.com/serra/5574343).



## Custom Domain Name
Currently this site is hosted under [[https://github.com/Neil-Penning/Neil-Penning.github.io]].
I want to host it under the domain [[https://blog.penning.solutions]].
[This github post](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site#configuring-a-subdomain) details how to do it.




# Development Environment
## Version Control
The site is deployed from the `master` branch. 
## Tmuxinator
## Neovim

# Writing Structure
