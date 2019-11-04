---
id: 11
title: 'Xaraya import: Optimization problem'
date: 2006-11-11T02:10:32+00:00
author: caphun
layout: post
guid: http://yelotofu.com/blog/?p=4
permalink: /2006/11/xaraya-import-optimization/
dsq_thread_id:
  - "1790609622"
categories:
  - PHP
tags:
  - optimization
  - xaraya
---
I recently created import scripts to migrate a forum containing 25,000 users, 50,000 topics & 650,000 posts to Xaraya. The scripts are based on **import_phpBB by mikespub**, which comes with the core, found in _/tools/import/_. After completing modifications to the scripts I did an import but was hit back hard by the speed it took to complete. I noticed a strange trend that as the number of processed rows increased the number or rows the script could process per hour decreased. To be honest, I wasn&#8217;t expecting anything quick due to the large amount of data to process, but after leaving it to run for 29 hours without any intention of finishing I had to put an end to this.

After some investigation into the cause of this slow down, I found the culprit was to do with an OPTIMIZE TABLE query at the end of each script. It makes sense, as the number of rows increased the longer it took to optimize the table. After removing all OPTIMIZE TABLE calls it took less than 12 hours to complete an import. This flaw is inherit in all import scripts under the tools section.

According to MySQL, OPTIMIZE TABLE is rarely needed and really only if large amounts of rows were removed or changed. Hereâ€™s what MySQL has to say about [OPTIMIZE TABLE](http://dev.mysql.com/doc/refman/5.0/en/optimize-table.html)

I collated all OPTIMIZE TABLE calls and moved to the Clean Up stage. Now, everything works fine and speedily!