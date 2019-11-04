---
id: 676
title: 'HowTo: Revert local changes in Git'
date: 2010-08-28T18:06:06+00:00
author: caphun
layout: post
guid: http://yelotofu.com/?p=676
permalink: /2010/08/howto-revert-local-changes-git/
dsq_thread_id:
  - "1241819812"
dsq_needs_sync:
  - "1"
categories:
  - Ramblings
tags:
  - checkout
  - git
  - reset
  - revert
---
Found [this answer](http://stackoverflow.com/questions/1146973/how-to-revert-all-local-changes-in-a-git-managed-project-to-previous-state/1146981#1146981) on Stack Overflow very useful, so thought I&#8217;d share it here:

> If you want to revert changes made to your working copy, do this:
> 
> `git checkout .`
> 
> If you want to revert changes made to the index (i.e., that you have added), do this:
> 
> `git reset`
> 
> If you want to revert a change that you have committed, do this:
> 
> `git revert ...`

<small><strong>Source:</strong> <a href="http://stackoverflow.com/questions/1146973/how-to-revert-all-local-changes-in-a-git-managed-project-to-previous-state/1146981#1146981">How to revert all local changes in a GIT managed project to previous state ?</a></small>