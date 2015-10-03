---
layout: post
title:  "Welcome to Jekyll!"
date:   2015-10-03 10:55:19
categories: jekyll update
---

Setting up github pages blog on Ubuntu 14.04
============================================


1 - Prerequisites: urgent need for blogging, ruby >= 2.0, github account (free), beverage of choice
------------------------------------------------------------------------------

Okay so let's say you are like me and you want to create a blog and you're tired of WordPress or whatever and just want a simple way to hack out some notes and stuff in your favorite editor and post it easily for posterity.  I'm running Ubuntu 14.04 at the moment so these instructions are specific to that but this stuff is pretty platform agnostic. Hopefully you know some [markdown](https://daringfireball.net/projects/markdown/syntax) but don't worry, you'll pick it up (I'm currently barely proficient with MD).

Ubuntu 14.04 comes with ruby 1.9 which isn't supported anymore by jekyll (sorry, I know, immediate dependency hell). Better get used to it (or you can just leave and go back to coding all your own stuff in C)
First install Ruby >= 2.0 - http://askubuntu.com/a/452293/62223
	`sudo add-apt-repository ppa:brightbox/ruby-ng
	sudo apt-get update
	sudo apt-get install ruby2.2`

You'll also need this to install github-pages (needed to build native extensions)
	`sudo apt-get install ruby-dev`

If you get an error like "ERROR:  Error installing github-pages  ERROR: Failed to build gem native extension" then you don't have the right ruby-dev version installed. I had originally installed ruby-dev but then realized that I needed to remove that and install the correct version which in my case was ruby2.2-dev. See [Failed to build gem native extension · Issue #133 · github](https://github.com/github/pages-gem/issues/133)

2 - Basic setup
---------------
Follow github pages setup instructions to create repo (add license, README, etc) then clone - https://pages.github.com/
	my github username is 'dwheaton' so I'll give the commands I used and you'll want to substitute your username...
	First I created the dwheaton.github.io repository
	I immediately regretted not taking github up on the offer to add LICENSE.md, README.md, and .gitignore files when I had to create them manually
	Then on my local system I cloned the new repo with: `git clone https://github.com/dwheaton/dwheaton.github.io`
	Immediately start hacking out the index.html file with instructions on how to do this.

Congratulations you now have now created yet another lame blog

3 - Jekyll
-----------

In order to make your blog less lame you're going to need to work on it and you need to install Jekyll on your local system to make that more convenient. Sure you could skip this but then you're unable to preview your changes easily before committing them to github.

This tutorial helped to get me started:
* [Build A Blog With Jekyll And GitHub Pages - smashingmagazine.com](http://www.smashingmagazine.com/2014/08/build-blog-jekyll-github-pages/)
* If you want a much easier quick-start process then head over to [barryclark/jekyll-now · GitHub](https://github.com/barryclark/jekyll-now) to "Build a Jekyll blog in minutes, without touching the command line."

Follow using Jekyll with github pages instructions (Gemfile, etc) - https://help.github.com/articles/using-jekyll-with-pages/
	sudo gem install bundler
	Setup Gemfile with github-pages
	bundle install

I ran jekyll new . and the customized the `_config.yml` and welcome post in the `_posts` directory

Finally you're done! Run `jekyll serve --watch` and you can view your site at [locahost:4000](localhost:4000). Actually, just kidding, if you're like me you got an error "Could not find a JavaScript runtime" and SUPRISE, you have to install that. Go ahead and grumble while you `sudo apt-get install nodejs` (seriously, you didn't think you'd actually get out of here without upgrading ruby and installing NodeJS). re-run jekyll serve. TADA!

Probably want to peruse the [Jekyll Docs](http://jekyllrb.com/docs/frontmatter/)
Might as well make sure you're aquainted with [YAML](http://yaml.org/) as well ;-)

Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll’s dedicated Help repository][jekyll-help].

[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
