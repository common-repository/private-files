=== Private Files ===
Contributors: jamesdlow
Donate link: https://www.paypal.com/cgi-bin/webscr?cmd=_xclick&business=K6VKWB3HZB2T2&item_name=Donation%20to%20jameslow%2ecom&currency_code=USD&bn=PP%2dDonationsBF&charset=UTF%2d8
Tags: private, files, proxy, logged, in, user, protect, download
Requires at least: 2.0.2
Tested up to: 2.8.4
Stable tag: 0.40

Private Files makes sure only logged in users can see images and file attachments.

== Description ==

There are several plugins to make a blog private, making it a good tool for basic collaboration / group ware. However file attachments / images have still been visible too the public, until now.



Private files acts as a proxy, making sure users are logged in before they can download any files. The nice thing about is, it doesn't modify the current uploads at all, doesn't store files in a different place, so if you want to stop using it, all links to files stay the same, so you don't need to redo anything.

How this plugin works 

1) It requires mod_rewrite/php running in apache, probably on unix/linux, although windows may work. 

2) It requires wordpress to be handling all url requests via a .htaccess in your blog root, and for your uploads to be a subdirectory of the your blog root and you're not using the default permalinks (ie. not http://www.myblog.com/?p=123)

3) An additional .htaccess file is placed in your uploads directory with the following content: 

	RewriteEngine On

	RewriteBase /wordpress/wp-content/uploads

	RewriteRule . /wordpress/afilethatshouldnotexist.txt

	Options -Indexes 



4) All requests for files within your upload are direct to a file that doesn't exist 

5) Wordpress handles this as a 404 error 

6) This plugin has a hook which intercepts the 404, and returns the file if the user is logged in. 

7) If you want to force user login please try Angsuman's Authenticated WordPress Plugin (http://blog.taragana.com/index.php/archive/angsumans-authenticated-wordpress-plugin-password-protection-for-your-wordpress-blog/) or Allow Categories (http://jameslow.com/2007/12/02/allow-categories/) to permission your blog. 

8) There's a small chance that the protection detection might be wrong, if so reprotect your files. 

9) If you want to stop using the plugin, unprotect it, or delete the .htaccess file with your uploads directory.

More information and the latest version can be found here:
http://jameslow.com/2008/01/28/private-files/

== Installation ==

1. Download privatefiles.php and place in wp-content/plugins
2. Log into your WordPress admin panel
3. Go to Plugins and "Activate" the plugin
4. Go to Manage->Private Files and click protect

== Frequently Asked Questions ==

== Screenshots ==
