layout: post
title: Getting Started Blogging with Hexo
date: '2020-03-15 23:22'
categories:
  - Hexo
---
<!-- TOC -->

- [Installing Hexo](#installing-hexo)
  - [Install Homebrew](#install-homebrew)
  - [Install Node.js](#install-nodejs)
  - [Install Hexo](#install-hexo)
- [Setting up first site template](#setting-up-first-site-template)
- [Installing a theme](#installing-a-theme)
- [Writing first content to get going](#writing-first-content-to-get-going)
- [Setting yourself up with GitHub for Hexo](#setting-yourself-up-with-github-for-hexo)
- [Deploying the Hexo site to GitHub](#deploying-the-hexo-site-to-github)
- [Trying a few plugins](#trying-a-few-plugins)
- [Maintaining the blog](#maintaining-the-blog)
- [Markdown Cheatsheet](#markdown-cheatsheet)

<!-- /TOC -->

This website is my personal blog and is intentionally minimal, lightweight and simple. (Reasons on why coming in a future blog post). It has been built with [`Hexo`](https://hexo.io), deployed with [`Git`](https://git-scm.com) and hosted on [`GitHub Pages`](https://pages.github.com). Eventually I might look in to setting up a custom URL domain and hosting elsewhere but the whole idea of this project was to keep things really simple, have an easy place to call home on the internet and publish blog posts with minimal fuss.

I researched static website generators a bit and settled on **Hexo**. There are other ‘blog frameworks’ available like [Jekyll](https://jekyllrb.com) and [Hugo](https://gohugo.io) which are well featured and supported, but I settled on Hexo for its apparent ease of use, my own familiarity with JavaScript and Markdown and a very simple deployment process which relies on nothing but a few simple terminal commands.

There are many guides to getting set up using Hexo online however in setting up this blog initially I had to gather info from various tutorials around the web and figure a few things out for myself.

This (first!) blog post attempts to bring all that knowledge together. It’s a long post but intentionally it’s just *one post* to keep everything together and provides, I hope, a complete guide to getting started.

Note - I am using **Mac OS X** as my platform of choice so bits of this guide will be specific to Mac. I imagine the set up for Linux is very similar. For Windows I imagine it’s quite similar and you can follow many of the steps, but I’m not a Windows user and so I’m afraid you’re on your own there, sorry! :)

---

## Installing Hexo
Hexo is a *’blogging framework’* which basically means it’s a bunch of tools for building simple webpages like this one. Using Node.js as a backbone, Hexo translates simple Markdown files in to well formatted HTML and bundles that together with some fancy CSS and JavaScript to create your published static webpage.

We have a bit of a ladder of installs to do here to get all we need to get going but the basic process to install Hexo is to install in the following order:

### Install Homebrew

Homebrew is a package manager for OS X that makes installing all kind of tools, packages and “linuxy things” a breeze. I already have that installed and if you’re reading this and have an interest in this kind of think i’m pretty sure you already have that set up too so we’ll skip over all the details, but as a simple reference run in a terminal:

    $ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"

You can verify it’s all OK by checking the version of Homebrew you’ve just installed:

    $ brew -v

### Install Node.js

Node.js is a JavaScript framework that basically allows you to run JavaScript outside of a browser (eg in a Terminal). The main thing we’re getting out of this that’s useful to us right now is a tool called `npm` (the **N**ode **P**ackage **M**anager). This is what we will use to install Hexo itself.

    $ brew install node

Verify it’s all working by checking the version of npm installed:

    $ npm -v

### Install Hexo

With Node.js and npm installed we can finally install Hexo itself:

    $ npm install hexo-cli -g

to check you’re good to go run:

    $ hexo -v


## Setting up first site template
Yay! We’re ready to go blogging. To kick things off, set up a new directory on disk somewhere sensible and in a terminal navigate there and run:

    $ hexo init NameOfMyAwesomeBlog

This will download various bits and bobs and set up all the directory structure you need for your website. The structure will look a bit like this:

	.
	├── _config.yml
	├── node_modules
	├── package-lock.json
	├── package.json
	├── scaffolds
	│   ├── draft.md
	│   ├── page.md
	│   └── post.md
	├── source
	│   ├── _drafts
	│   ├── _posts
	│   ├── about
	│   ├── images
	└── themes
	    └── landscape

`_config.yml` as the name suggests is a really important file and defines a lot of the technical working of the blog. We’ll edit it in a bit once we’ve set up some git stuff below.

One of the beauties of Hexo is you don’t have to touch most of this stuff. You’ll dig in to `source` a bit when creating posts and `themes` initially to set up the look of the pages and whenever you want to tweak things like the js or css of your site, but you shouldn’t need to do much with themes once you find one you like. You can mess around with `scaffolds` if you like but it’s not really needed and the other stuff I frankly don’t need to touch at all.

We don’t even have to build or deploy the site to the web to see it in action. Hexo comes with a way to preview the webpage locally very easily. To install the server package run:

	$ npm install hexo-server --save

and then:

	$ hexo server --draft --open

This will host your page at `http://localhost:4000` and launch your web browser with your site in its current state. The `--draft` flag tells hexo to view both published and draft posts (see below). If you want to preview just the actual published content to see how your site will look to the outside world when deployed and not draft posts you can remove this flag.

When you install Hexo it comes with its own default website template called **landscape**. It’s OK but not very inspiring and you’ll probably want to choose your own later, however landscape is what we’re seeing now:

![](images/2020/03/hexo_landscape_002.jpg)

If you’re seeing something like this you’re in great shape and everything has installed correctly.

## Installing a theme
I like a nice photo of planet Earth as much as the next person but before getting in to the process of writing posts I wanted to get a theme for my site that looked a bit better and more in keeping with the aims of this site to be simple, uncluttered and minimal. I chose [**Cactus**](https://github.com/probberechts/hexo-theme-cactus) by GitHub user probberechts (thanks!).

From the root of your blog directory (the directory with the _config.yml file in it) run:

    $ git clone https://github.com/probberechts/hexo-theme-cactus.git themes/cactus

This will copy the theme in to the right place. Then open up `_config.yml` in a text editor and edit the line about theme, comment out landscape and set cactus:

    # theme: landscape
    theme: cactus

Cactus also comes with 4 color options: white, classic, light and dark. I chose light. Add this below where you just set the theme in `_config.yml`:

    theme_config:
      colorscheme: light

If you refresh your webpage in your browser now you won’t see the change. Anytime you edit `_config.yml` you need to restart the hexo server. If you rerun:

    $ hexo server --draft --open

You’ll see the changes and your new theme. You can dig in to the files in `./themes/cactus/` on your own to customize your page. The readme from probberechts on his Cactus theme’s GitHub page is really helpful too.

## Writing first content to get going
If you’ve got this far you’re probably well and truly ready to start writing posts.

Hexo has a nice system whereby you can work on drafts of posts and not have them published when you build and deploy your scene until you’re ready to, it’s a good habit to get in to. To create a post run from the root directory of your blog:

    $ hexo new draft myPostName.md

This will create a post in somewhere like:

    ~/PATH/TO/BLOG/.../source/_drafts/myPostName.md

I won’t go in to how to write in Markdown here, you can see the cheatsheet at the bottom of this post and hundreds of other resources online for better advice on that. Markdown is a fantastically intuitive way to write for the web and I highly recommend spending some time learning how to use it. It’s really quite simple and will serve you well beyond writing posts for your blog - it can become a very efficient way of writing notes and documents in many situations.

When you’re happy with your draft you can ‘publish’ the post which will move it from `_drafts`, a folder which doesn’t get included when you generate your site, in to `_posts`, which does. Run:

	$ hexo publish myPostName

The ‘title matter’ of the markdown post will also get a timestamp now added with the publish date and time.

## Setting yourself up with GitHub for Hexo
I started writing something for this section but found myself basically copying this blog post:

[http://jr0cket.co.uk/hexo/managing-hexo-website-content-with-git-and-github.html](http://jr0cket.co.uk/hexo/managing-hexo-website-content-with-git-and-github.html)

Follow these instructions and you’ll get set up in no time.
## Deploying the Hexo site to GitHub
To build your site simply run the command:

	$ hexo generate

and when you’re ready to deploy to the web:

	$ hexo deploy

You can also combine these two commands in to one if you want to run them together:

	$ hexo deploy --generate

## Trying a few plugins
Plugins are ways of extending the functionality of Hexo. There are hundreds available, some are very powerful and some much more niche but all add new features to your Hexo set up.

I added a search page to this site very simply. First install the search plugin:

	$ npm install hexo-generator-search --save

Then create a new page for the search to live in:

	$ hexo new page search

this will create a new `index.md` page at `./source/search/` edit this file to add the search type:

	---
	title: Search
	type: search
	---

Then to configure theme’s main `_config.yml` (in `./themes/cactus/_config.yml` in my case) to include it:

	nav:
	  search: /search/

As another example, a simple plugin exists to be able to include emoji in your posts. Install the plugin:

	$ npm install hexo-filter-github-emojis --save

This plugin needs a little bit more configuration. Edit your site’s main `_config.yml` file (the one at the sites root, not theme) to include:

	githubEmojis:
	  enable: true
	  className: github-emoji
	  inject: true
	  styles:
	  customEmojis:

Now you can add emojis with the usual GitHub syntax of a `:` on each side of the emoji name eg `:thumbsup:` {% github_emoji thumbsup %}

A useful Emoji cheatsheet lives {% github_emoji point_right %}[here](https://www.webfx.com/tools/emoji-cheat-sheet/){% github_emoji point_left %}

## Maintaining the blog
Maintaining the blog is very simple too. Just run the command:

	$ hexo clean

to remove any previously built sites that are living in your root directory (don’t worry, everything is backed up and version controlled on Git - that’s the whole point of this system) and then generate and deploy your new site:

	$ hexo generate --deploy


## Markdown Cheatsheet

![](images/2020/03/markdown_cheatsheet.jpg)

---
