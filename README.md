# Knitr-Hyde

## Introduction

The aim of this project is to help prospective R-bloggers.  If you have a particular Git Hub project that deals with R and you want to blog a bit about your work as it develops, then you can use the material from my `knitr-hyde` repository to set up a Jekyll-powered site with good styling borrowed from Mark Otto's [Hyde project]() with a minimum of fuss.  With help from Yihui Xie's [`servr`](https://github.com/yihui/servr) package and [knitr-jekyll](https://github.com/yihui/knitr-jekyll) code you 'll be able to write your posts in R Markdown, build and preview the site locally, and push to your Git Hub Pages project site when you are ready.

I have tried to minimize what you need to know about Jekyll (and web development generally) in order to get going.  You can learn more about Jekyll when it suits you and eventually make thorough-going alterations to my blog-template, but for now I want you to be able to concentrate on getting your content out there to a waiting public.

## Preliminaries

### Platform

Jekyll is not officially supported on Windows, so you had best try this with Mac OSX or a Linux distribution.

### Get My Files

If you don't already have an existing project, then fork my [knitr-hyde](https://github.com/homerhanumat/knitr-hyde) repository from Git Hub, rename it as yo wish and then clone it on your own machine.  You can do your project work on the `master` branch and switch to the `gh-pages` branch for blogging.

If you already have  project repository on Git Hub, then simply create a `gh-pages` branch, delete all of the files, download a [zip file](https://github.com/homerhanumat/knitr-hyde/archive/gh-pages.zip) of my `gh-pages` branch and extract it into your repo while you have your `gh-pages` branch checked out.

### Get the Packages

### Ruby and Gems

You will need to install [Ruby](https://www.ruby-lang.org/en/downloads/), and then install the [Jekyll](http://jekyllrb.com/) gem.  It's best if you install the same version of Jekyll that Git Hub will use to build your page.  You can find the current version [here](https://pages.github.com/versions/).  At the time of writing this is version 2.4.0, so from the command line run:

```
sudo gem install jekyll -v 2.4.0
```

You'll also want a gem that keeps all dependencies of Jekyll at the same version level as used by Git Hub:

```
sudo gem install gh-pages
```

In order to stay current with Git Hub, update this gem frequently:

```
sudo gem update gh-pages
```

### The servr Package

You'll need Yihui Xie's `servr` package.  In R, run:


```
install.packages("servr")
```

## Configuration

Make sure you are on the `gh-pages` branch.  In the root directory, locate the `_config.yaml` file.  Make some choices:

* Change the `title` and `description`.
* Change the values of `baseurl` and `baseurlstrip` to the name of your project repository.  Make sure there is a trailing '/' at the end of `baseurl`, but not at the end of `baseurlstrip`.
* Change `url`.  Since you are pushing to Git Hub, it can be `https://yourgithubusername.github.io`.
* Decide if you would like people to be able to comment on your posts.  If you want this, leave `disqus` at `true` and register at the [Disqus site](https://disqus.com/).  You will have the opportunity to add Disqus to your site.  Do this.  As part of this process you will be asked to create a *shortname* for your site.  Set `shortname` accordingly.  If you don't want commenting, simply set `disqus` to `false`.
* Change `twitter` and `facebook` to `false` if you don't want Tweet and Facebook Share buttons for your posts.

## Authoring

From the `_source` folder, find an R Markdown document and open it.  You'll see YAML front-matter at the beginning, like this:


```
layout:  post
title: "Sample Post"
comments:  true
published:  true
author: "Homer White"
date: 2015-12-12 20:00:00
categories: [R]
output:
  html_document:
    mathjax:  default
    fig_caption:  true
```

Set the title, author and date as you wish.  If you post has categories, fill them in, for example:

```
categories:  [R, 'Unruly Rants', 'Marsupial Studies']
```

Save the post using the date-and-title format:

> `year-mm-dd-your-brief-post-title.Rmd`

Write your post.  As you go, you can run the R command:


```
servr::jekyll()
```

If you are using R Studio then the site will show up in the Viewer.  Every time you save a change to your draft post, the site will re-build, so you can preview your change in real time.  That's the genius of Yihui Xie.

The post will be rendered using version 1.9 of the Ruby gem `kramdown`.  Look in my `sample-post` for examples of inline and displayed mathematics.  Otherwise you can write pretty as you normally do in R Markdown.

When you are happy with your post, commit your changes and push your `gh-pages` branch to Git Hub.  You can view your site online at:

> https://yourgithubusername.github.io/yourProjectName

## Further Customization

Make the site entirely your own by erasing my posts.  Delete the unwanted R Markdown sources, and delete their processed Markdown derivatives from the `_posts` folder.

Styling is provided from Mark Otto's excellent Hyde project.  Hyde comes with eight themes, and you can put the sidebar on the right if you like.  Consult the [Hyde project](https://github.com/poole/hyde) README to learn how to make these changes.

If you know a bit of CSS then you might want to play around with the  `public/css/custom.css` file.

Eventually you should learn more about Jekyll, and especially the [Liquid](http://liquidmarkup.org/) templating system that Jekyll supports.  Then you can customize the site even further, for example by adding your own sidebar widgets.