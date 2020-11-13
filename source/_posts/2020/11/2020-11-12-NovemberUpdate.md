layout: "post"
title: "November Update"
date: "2020-11-12 21:30"
---

Quick Post testing Hexo still works after updating to v5.2.0!

:smiley:

I want to try and start up the Weeknotes again and I have a couple of ideas for longer blog posts. It was a bit annoying to forget all my commands and git backup procedure, so here is a cheatsheet for future.

## Updating Node.js
I have 'n' installed which makes this very easy. Simply run:

    $ n latest

This grabs the latest bleeding edge version of Node.js (currently 15.2). Alternatively to grab the latest stable version run:

    $ n lts

## Updating Hexo
Navigate to the Hexo folder of the blog and open the package.json file and change the line in dependencies:

    "dependencies": {
        "hexo": "^4.1.0",      <- remove this line
        "hexo": "^5.2.0",      <- replace with this line

Then run:

    $ npm update

After, confirm Hexo has updated correctly with:

    $ hexo --version

## Backup to GitHub

After deploying the site with Hexo, I usually backup the working directory to GitHub as well so that I can pull it down to my other machine (laptop) and work on other posts keeping both local computers in sync. On the machine that's just published the web site I run:

    $ git add .
    $ git commit -m "backup <DATE>"
    $ git push origin backup

Then on my other machine I run a simple pull:

    $ git pull

If the two computers are out of sync I might have to push from both machines and then pull down to them both to make sure they're both up to date with the HEAD of the branch.

---
