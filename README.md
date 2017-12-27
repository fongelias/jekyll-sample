# jekyll-sample
a jekyll static site generation sample

## what is jekyll?
a static site generator that converts raw files into a ready-to-ship static site

## installation
`gem install jekyll bundler`

installs jekyll as well as bundler (a gem management gem).
If you are using OSX, like I am, you may run into this error:

`You don't have write permissions for the /Library/Ruby/Gems/2.0.0 directory.`

this probably means that you are trying to install gems on the OSX managed version of ruby. This is not recommended, and you should use homebrew to install ruby first:

`brew install ruby`

You'll want to use rbenv to manage this version of ruby:

`brew install rbenv`

Run rbenv doctor to see if it is installed properly, and follow the commands to finish the installation:

`curl -fsSL https://github.com/rbenv/rbenv-installer/raw/master/bin/rbenv-doctor | bash`

Load it manually:

`rbenv init`

if you are still getting the same error, run the following and make sure that the version is not set to "system":

`rbenv version`

if it is, change the version to your rbenv managed ruby. In my case, I am using 2.2.5, and setting the version locally (as opposed to globally):

`rbenv local 2.2.5`

## starting a new project
Run the following in the parent directory of where you want your project to be:

`jekyll new [project-name]`

this will create a directory at ./[project-name] with a few different files:

`_config.yml
_posts/
404.html
about.md
Gemfile
Gemfile.lock
index.md`

if you cd into ./[project-name], and run the following:

`bundle exec jekyll serve`

it will generate a `_site/` directory from your source, and serve it on `localhost:4000`. You can try this to see what the defaults look like.

### What are all these files?

#### [_config.yml](https://jekyllrb.com/docs/configuration/)
stores configuration data. You can configure the jekyll build here, as well as set global variables.

#### _posts/
directory for your dynamic content! files in here need to follow the following naming convention:

`YEAR-MONTH-DAY-title.markdown`

##### writing a post
The start of each post must have [YAML Front Matter](https://jekyllrb.com/docs/frontmatter/), which is a little header that looks like this:

`
---
layout: post
title: some title here
---
`
the YAML Front Matter is where you set variables that can be accessed in the post, or in other layouts that include the post later on.

below this header, you can write the content of your post.

to include an image, you use the following syntax:
![image name]({{ "file/path.jpg" | absolute_url}})

or without the "!", it appears as a link to the path

to highlight a code snippet:
`
{% highlight ruby %}
def show
	some code here
end
{% endhighlight %}
`
##### showing a list of posts
example for creating a list of posts
`
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
`

#### index.html/index.md









