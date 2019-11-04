---
id: 10
title: 'RoR &#038; SVN cross-platform development'
date: 2006-04-02T15:30:39+00:00
author: caphun
layout: post
guid: http://yelotofu.com/blog/?p=3
permalink: /2006/04/rubyonrails-svn-development/
categories:
  - Ruby on Rails
tags:
  - rubyonrails
  - svn
  - unix
  - windows
---
In a normal development environment you&#8217;re likely to have developers working on different OS platforms to your server or in some cases, especially with remote working, you&#8217;d have developers working on different OS platforms to each other. With RoR this is probably more so as most developers I know use WindowsXP as their preferred development environment whereas Rails is normally served off a *nix box. Due to these setups cross-platform compatibility issues are inevitable. Take my current project as an example. I am running WindowsXP whereas another developer in my team is using MacOSX, which is a <a href="http://en.wikipedia.org/wiki/Unix-like" target="_blank">Unix-like</a> operating system. Whenever we share files over SVN rails starts to complain about EOL (End Of Line) problems or not being able to detect the EOL. This is due to the fact that Windows and Unix-like OS use different EOL styles and do not share common file attributes.

The resolution is simple and it&#8217;s on the SVN side. Set **svn:executable** and **svn:eol-style** properties of _/public/dispatch.fcgi_ and all files within the _/scripts/_ folder to:

svn:executable = *  
svn:eol-style = native

Now, Commit changes and Update local SVN files.

If errors persist and is along the lines of, _&#8220;rake, rakefile cannot be found&#8221;_ when running rake or, _&#8220;Ruby bin folder cannot be found&#8221;_ when running the project then try the following:

  1. Open up _dispatch.fcgi_
  2. Insert a blank line at the end of the file, re-save and Commit the file.

The above ensures that the repository is correctly updated with the latest file when you Commit.