---
id: 20
title: 'Quick tip: upload_tmp_dir on Win2k'
date: 2007-02-08T18:49:45+00:00
author: caphun
layout: post
guid: http://yelotofu.com/2007/02/quick-tip-upload_tmp_dir-on-win2k/
permalink: /2007/02/quick-tip-upload_tmp_dir-on-win2k/
categories:
  - PHP
tags:
  - PHP
  - upload_tmp_dir
  - win2k
---
If you are running PHP as a module on a Win2k server remember to set the `upload_tmp_dir` in your `php.ini` to a folder that allows the Anonymous Internet User read/write permissions. Otherwise you&#8217;d end up with 0.0 byte files when performing PHP uploads&#8230;By default the `upload_tmp_dir` is set to `%windir%temp` if no value is given. This system folder is normally restricted to known Admin and User accounts only, hence files that are uploaded via PHP are not saved to the filesystem. You may notice **stat failed** warnings if you try performing file operations on uploaded files.

To resolve this problem you should either give Anonymous users access to the `%windir%temp` folder (not recommended) or create a folder in `D:uploads`, if you have a D drive that is, and point your `upload_tmp_dir` to it, then give Anonymous users access to the new folder.