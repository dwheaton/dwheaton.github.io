---
layout: post
title:  "Setting up github pages on Ubuntu 14.04"
date:   2015-10-02 21:32:00
categories: jekyll github ubuntu 14.04
---

Once you get the below setup you will be able to update your website with the following easy steps:
0. Open a terminal
1. Create/edit a file in your favorite editor
2. Use git to add, commit, and push your changes
> If this doesn't sound easy to you then you should probably use a different blogging platform or site-builder

1 - Prerequisites: urgent need for blogging, ruby >= 2.0, github account (free), beverage of choice
------------------------------------------------------------------------------

Okay so let's say you are like me and you want to create a bloggy site and you're tired of WordPress or whatever. You just want a simple way to hack out some notes and stuff in your favorite editor and post it easily for posterity.  I'm running Ubuntu 14.04 at the moment so these instructions are specific to that but this stuff is pretty platform agnostic. Hopefully you know some [markdown](https://daringfireball.net/projects/markdown/syntax) but don't worry, you'll pick it up (I'm currently barely proficient with it which is fine).

First of all, Ubuntu 14.04 comes with ruby 1.9 which isn't supported (anymore) by jekyll. Oh joy: immediate dependency hell... *shrug* better get used to it!

First install Ruby >= 2.0

	sudo add-apt-repository ppa:brightbox/ruby-ng
	sudo apt-get update
	sudo apt-get install ruby2.2

See: [Install ruby 2.0 without ruby-switch? - Ask Ubuntu](http://askubuntu.com/a/452293/62223)

You'll also need ruby-dev to install github-pages (needed to build native extensions)

	sudo apt-get install ruby2.2-dev

If you get an error like this later in step 3

	ERROR:  Error installing github-pages
	ERROR: Failed to build gem native extension

then you don't have the right ruby-dev version installed.

> In my case: I had originally installed ruby-dev before I realized that the default ruby 1.9 wasn't adequate so I had to go back and remove ruby-dev and install the correct version to match my ruby (ruby2.2-dev in my case). See: [Failed to build gem native extension · Issue #133 · github](https://github.com/github/pages-gem/issues/133)


2 - Setup Github site repo
---------------
You'll need to follow these [github pages setup instructions](https://pages.github.com/) to create your github site repository for your username (add license, README, etc). Then you clone it to your local system.

> Replace USERNAME in the below instructions with your actual github username.

1. Create your new USERNAME.github.io repo on github.com. You should probably follow convention and go ahead and allow github to create the standard LICENSE.md, README.md, and .gitignore files for you so you don't have to add them later.
2. On your local system you can now clone the new repo with: `git clone https://github.com/USERNAME/USERNAME.github.io`
3. Immediately start hacking out a basic index.html file.
4. Commit and push to publish your changes to your new site which can be accessed at `http://USERNAME.github.io`

**Congratulations you now have now created yet another lame blog!**


3 - Install and configure Jekyll
-----------

Okay so let's face it: your site needs some work!

Enter [Jekyll](https://jekyllrb.com/) which "is a blog-aware, static site generator" and as such will hopefully make your life easier and more convenient. Sure you could skip this but then you don't get any help from a framework and you're unable to easily preview your changes easily before committing them to github.

This tutorial helped to get me started:

* [Build A Blog With Jekyll And GitHub Pages - smashingmagazine.com](http://www.smashingmagazine.com/2014/08/build-blog-jekyll-github-pages/)
* If you want a much easier quick-start process then head over to [barryclark/jekyll-now · GitHub](https://github.com/barryclark/jekyll-now) to "Build a Jekyll blog in minutes, without touching the command line." If you got this far you're probably comfortable with the command line and reading the docs yourself so I suggest forging on and embracing the command line.

Follow [Using Jekyll with Pages - User Documentation - GitHub Help](https://help.github.com/articles/using-jekyll-with-pages/) instructions:

	sudo gem install bundler
	Setup Gemfile with github-pages
	bundle install

With Jekyll installed you can now run `jekyll new .` and then customiz the `_config.yml` and welcome post in the `_posts` directory.

You are finally done! Go ahead and run `jekyll serve --watch` and you can preview your site at [locahost:4000](localhost:4000).

> Actually, just kidding, if you're like me you got an error "Could not find a JavaScript runtime" and SUPRISE, you have to install one more thing :-P

Go ahead and grumble while you `sudo apt-get install nodejs` (seriously, you didn't think you'd actually get out of here without upgrading ruby and installing NodeJS). re-run jekyll serve. TADA!

4 - Commit and push to publish
---------------------------

Now you reap the benefits of your labors. Sip your beverage while you easily add posts, preview them using locally, and then simply commit and push to publish to your github page. There is a lot more to learn over at the [Jekyll Docs](http://jekyllrb.com/docs/frontmatter/). Have fun!
