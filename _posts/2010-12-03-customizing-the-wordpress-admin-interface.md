---
id: 739
title: Customizing the WordPress Admin Interface
date: 2010-12-03T15:22:12+00:00
author: caphun
layout: post
guid: http://yelotofu.com/?p=739
permalink: /2010/12/customizing-the-wordpress-admin-interface/
dsq_thread_id:
  - "1241819047"
dsq_needs_sync:
  - "1"
categories:
  - WordPress
---
[Six Revisions](http://sixrevisions.com/) have an excellent post on [how to customize the WordPress admin area](http://sixrevisions.com/wordpress/how-to-customize-the-wordpress-admin-area/).

However I was looking also at a way of removing the Plugin Editor menu and noticed you can&#8217;t remove it like you do with the Theme Editor menu because it&#8217;s not added via an action. So I added this to my theme&#8217;s `functions.php`:

<pre language="php">add_action('_admin_menu', 'remove_plugin_editor_menu', 1);

if ( ! function_exists( 'remove_plugin_editor_menu') ):

function remove_plugin_editor_menu() {
  global $submenu;
  unset($submenu['plugins.php'][15]);
}

endif;
</pre>

It&#8217;s very hacky because I&#8217;m targetting the index value of the `$submenu` array. If anyone knows a better way then I&#8217;d love to here it!