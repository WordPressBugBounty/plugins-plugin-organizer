=== Plugin Organizer ===
Contributors: foomagoo
Donate link: https://www.sterupdesign.com/donate
Tags: plugin organizer, load order, organize plugins, plugin order, sort plugin, group plugin, disable plugins by post, disable plugins by page, disable plugins by custom post type, turn off plugins for post, turn off plugins for page, turn off plugins for custom post type
Requires at least: 4.6.0
Tested up to: 6.3.1
Stable tag: 10.1.10


This plugin allows you to do the following:
1. Change the order that your plugins are loaded.
2. Selectively disable plugins by any post type or wordpress managed URL.
3. Adds grouping to the plugin admin age.

== Description ==

This plugin allows you to do the following:
1. Change the order that your plugins are loaded.
2. Selectively disable plugins by any post type or wordpress managed URL.
3. Adds grouping to the plugin admin age.

WARNING: Reordering or disabling plugins can have catastrophic affects on your site.  It can cause issues with plugins and can render your site inaccessible.

== Installation ==

1. Extract the downloaded Zip file.
2. Upload the 'plugin-organizer' directory to the `/wp-content/plugins/` directory
3. Activate the plugin through the 'Plugins' menu in WordPress
4. Use the menu item under settings in the WordPress admin called Plugin Organizer to get the plugin set up.

IMPORTANT: To enable selective plugin loading you must move the /wp-content/plugins/plugin-organizer/lib/PluginOrganizerMU.class.php file to /wp-content/mu-plugins or wherever your mu-plugins folder is located.  If the mu-plugins directory does not exist you can create it.  The plugin will attempt to create this directory and move the file itself when activated.  Depending on your file permissions it may not be successful.

Note: If you are having troubles you can view the documentation by going to https://www.sterupdesign.com/dev/wordpress/plugins/plugin-organizer/documentation/

== Frequently Asked Questions ==

You can find a full FAQ list at https://www.sterupdesign.com/dev/wordpress/plugins/plugin-organizer/faq/

= Can Plugin Organizer be used with caching plugins? =

The simple answer. Yes. But you must understand how your caching plugin and Plugin Organizer do what they do. If your caching plugin creates a minified version of the javascript files loaded on a page then there is the potential that Plugin Organizer will cause the caching plugin to constantly recreate the minified javascript files.

Let�s say you have plugins A, B, C, and D active on your site and D is disabled globally. All 4 plugins add javascript to the site. On http://www.yourdomainnameyouuse.com/post-1/ you have plugin B disabled with Plugin Organizer. On http://www.yourdomainnameyouuse.com/post-2/ you have nothing disabled by Plugin Organizer and plugin D has been enabled, overriding the global setting. When someone visits http://www.yourdomainnameyouuse.com/post-1/ a minified javascript file has to be generated containing the scripts for plugins A and C. Then someone visits http://www.yourdomainnameyouuse.com/post-2/. The minified javascript file has to be recreated because the javascript for plugins A, B, C, and D need to be loaded. Then someone visits http://www.yourdomainnameyouuse.com/post-3/ and the minified javascript file has to be created again because the file has to contain the scripts for plugins A, B, and C but not D.

The above example explains how load time and caching can be affected with a caching plugin that creates minified javascript files. It basically renders the caching plugin useless.

Another example would be a caching plugin that creates a static version of pieces of the page. Again lets say we have the same plugins and the same posts. When someone visits http://www.yourdomainnameyouuse.com/post-1/ static pages are created with the content from plugins A and C. This cache has a lifetime of 300 seconds for example. When someone visits http://www.yourdomainnameyouuse.com/post-2/ it has the content for plugins A and C but it is missing Plugins B and D because the cache hasn�t expired. This can cause unexpected content and errors.

There are different ways that caching plugins work and they can work together with Plugin Organizer. These are only 2 examples to give an idea. But you have to understand how they work and how you are affecting your cache by disabling plugins.

= Are there any known conflicts with other plugins? =

Yes.  A malicious plugin named WP Spamshield targets the settings used by Plugin Organizer to disable it.  It also targets various other plugins and changes how they behave or disables them entirely.  All of this is done without the users knowledge or consent.  This plugin was removed from the Wordpress Plugin Directory because of this malicious code but it may still exist on some users sites.  It will also likely be released from a different repository in the future and start targeting plugins again.  You should remove WP Spamshield not only to make sure that Plugin Organizer runs correctly but to ensure the security of your website is not compromised.  Find out more at https://www.sterupdesign.com/blog/malware/wp-spamshield/.

= How do I disable plugins on the WordPress admin? =

Follow the documentation page for disable plugins on wp-admin.

= I upgraded and the metabox has disappeared from the post edit screen where I can enable/disable plugins. =

Go to the Plugin Organizer settings page and click the button under selective plugin loading to turn it on.  During the upgrade process selective plugin loading got turned off.

= How do I enable the selective plugin loading functionality? =

Go to the Plugin Organizer settings page and click the button under selective plugin loading to turn it on.  Then visit your homepage.  Finally return to the Plugin Organizer settings page and see if the button is still set to on.  If it is not then you are running an old version of the MU component.  Copy the PluginOrganizerMU.class.php file to the mu-plugins folder then deactivate and reactivate the plugin.  Repeat these steps to ensure that the plugin is working.  Remember that you will need to update the PluginOrganizerMU.class.php file whenever the plugin is updated and check your settings afterward.

= Does this plugin work with wordpress multi-site? =

Yes it has been tested on several multi-site installs.  Both subdomain and sub folder types.

= Does this plugin work with custom post types? =

Yes it has been tested with custom post types.  You can add support for your custom post types on the settings page.

= Does this only apply to WP MU or all types of WP installs? =

"IMPORTANT: To enable selective plugin loading you must move the /wp-content/plugins/plugin-organizer/lib/PluginOrganizerMU.class.php file to /wp-content/mu-plugins or wherever your mu-plugins folder is located. If the mu-plugins directory does not exist you can create it.  The plugin will attempt to create this directory and move the file itself when activated.  Depending on your file permissions it may not be successful."

The mu-plugins folder contains "Must Use" plugins that are loaded before regular plugins. The mu is not related to WordPress MU. This was added to regular WordPress in 3.0 I believe. I only placed this one class in the MU folder because I wanted to have my plugin run as a normal plugin so it could be disabled if needed. 

= In what instance would this plugin be useful? =

Example 1: If you have a large number of plugins and don't want them all to load for every page you can disable the unneeded plugins for each individual page.  Or you can globally disable them and enable them for each post or page you will need them on.
Example 2: If you have plugins that conflict with eachother then you can disable the plugins that are conflicting for each indivdual post or page.
Example 3: If you have plugins that conflict with eachother then you can disable the plugins globally and activate them only on posts or pages where they will be used.

Note: If you are having troubles you can view the documentation by going to https://www.sterupdesign.com/dev/wordpress/plugins/plugin-organizer/documentation/

= How do I target the homepage of my site if it isn't a page post type? =

Create a plugin filter with your home page url. Like https://www.sterupdesign.com/. Then enable or disable the plugins you want with that filter.

= Can I use wildcards in a plugin filter permalink? =

Yes. You can use limited wildcards in the permalink structure. For instance you can match the url https://www.sterupdesign.com/some/pretty/permalink/ by entering https://www.sterupdesign.com/some/*/permalink/. You can also match the url by entering https://www.sterupdesign.com/*/pretty/permalink/ as the permalink. The only character that is recognized is the * character. It can only replace one piece of the url in between the / characters.

= Can I enable/disable plugins based on post type? =

Yes. Go to the Post Type Plugins page under Plugin Organizer in the admin menu. Here you can select the post type you want to change and disable/enable plugins for that post type as long as the setting hasn't been overridden on the individual posts.

= How do I disable a plugin on the front end and still have it enabled on the admin pages? =

To load a plugin only in the admin you need to enable selective plugin loading for the admin areas and fuzzy url matching. Then globally disable the plugin you want to turn off on the front end. Next create a plugin filter with the permalink set to your admin url. Like https://www.sterupdesign.com/wp-admin/. Then enable the plugin for that plugin filter and select also affect children. Now the plugin should only be loaded in the admin.

= Can I disable plugins by role? =

Yes. Go to the Plugin Organizer settings page and check the box next to each of the roles you want to be able to disable/enable plugins with. THen a separate container will appear on the post edit screen for you to disable/enable plugins with.

= I have disabled a form plugin globally and enabled it on a specific page where it is used. The plugin loads on the page but then it doesn't work when I submit the form. =

When the form is submitted it is not submitting to the page you are viewing. It is submitting to an ajax endpoint. Which is a different URL. You need to enable the plugin on that URL to get the form working. Here are 2 examples of how to do that.

Caldera Forms:
https://wordpress.org/support/topic/conflict-w-caldera-forms-like-emilybkk-posted/

Contact Form 7:
https://wordpress.org/support/topic/conflict-with-contact-form-7-4/

== Screenshots ==

1. Settings page example.
2. Global plugins page.
3. Search plugins page.
4. Post type page.
5. Group and order plugins page.
6. Page edit screen.

== Changelog ==

= 10.1.10 =
Fixed PHP warning about array offset when the database returns a bad result in MU plugin

= 10.1.9 =
Restored code to use the $_SERVER array for the siteURL value if the right values are set and added in a fallback to use the wpurl option if they aren't.

= 10.1.8 =
Fixed PHP warnings in tpl/settings.php and lib/PluginOrganizerMU.class.php
Changed the base URL to use the setting for the Wordpress install instead of a server variable
Fixed ajax message container text being pushed to the side.

= 10.1.7 =
Fixed some PHP warnings for unset variables.
Fixed fatal error when a site doesn't have the plugin order saved on a mutlisite install and a plugin is deleted.

= 10.1.6 =
Fixed unset variable warnings.

= 10.1.5 =
Fixed unset variable warnings.

= 10.1.4 =
Fixed check for MU plugin class that throws warning in mu_plugin_notices class.

= 10.1.3 =
Changed the way the load order is maintained to use the directory name like the Wordpress core does instead of the plugin name.

= 10.1.2 =
Added check to see if active sites column has been hidden on the plugin admin page for network sites. If it's hidden the checks will not be performed.

= 10.1.1 =
Fixed a bug with the post type plugins page where the list of disabled plugins was not refreshed when changing to a different post type.

= 10.1 =
Added column to supported post types that indicates whether the post type settings have been overridden and also added a filter to only see posts of that type that have overridden those settings.
Fixed the also affect children and wildcard functionality so that they can be used together instead of only using one or the other on a plugin filter.
Added an admin alert that tells the user when selective plugin loading gets disabled due to the version numbers of the standard and MU plugins not matching.
Made the MU plugin only show an alert and bypass selective plugin loading rather than disabling it in the database when version numbers don't match.
Added a warning when more than one wildcard is entered in a plugin filter to let the user know that it is not supported.

= 10.0.1 =
Removing images that aren't used anymore.
Updating screenshots.

= 10.0 =
Created new interface to make managing plugins less confusing and get rid of the drag and drop interface.
Cleaned up CSS left over from older versions of the plugin.
Removed the custom CSS for the admin because it was becoming hard to maintain and can be achieved by adding CSS styles to your theme if needed.
Fixed missing nonce for the front end debug container ajax call.

= 9.7 =
Added column to network plugins page to indicate which sites a plugin is active on.
Fixed the recreate permalinks functionality so it will find plugin filters that need to be updated with new hashes or to indicate that the site uses a secure protocol.
Added better help text to the recreate permalinks tab on the settings page.
Changed the add_hooks function to only add admin hooks on the admin pages.
Fixed functionality to find and remove old plugin filters that are tied to posts that no longer exist.

= 9.6.4 =
Updating scripts to use my new domain name for documentation links so plugins like wordfence don't alert users.
Updating readme to reflect compatibility with WP 5.1.

.= 9.6.3 =
Added list of enabled plugins to the debug message for each page.

= 9.6.2 =
Fixed issue with visual editors not loading the Plugin Organizer meta box so post type plugins were not correctly applied.

= 9.6.1 =
Fixed a CSS issue where the jQuery UI styles were being loaded after the PO admin style so some styles were not being overridden properly.
Fixed the jQuery UI dialog header styling.

= 9.6 =
Changed from using wp_get_sites to get_sites to remove a deprecated message and stop using a deprecated function.
Added action calls to display the admin notices and debug messages in the Plugin Organizer meta box when on the post edit screen to ensure compatibility with the Gutenberg editor.

= 9.5.1 =
Added warning for users running Woocommerce and Woocommerce Smart Coupons.
Added ability to set the style of the debug messages container so it will work better with any site.

= 9.5 =
Changed all ajax functions to accept json objects in the response.
Changed footer action call for debug messages to use get_footer instead of wp_footer.

= 9.4 =
Added debug messages to see how the MU plugin is affecting the page a user is viewing. Messages can be restricted by role.
Changed the way settings are sent from the settings page to the ajax endpoint.

= 9.3.6 =
Fixed a problem with custom post types not applying the custom post type settings when they are created off of the edit screen.

= 9.3.5 =
Fixed colorpicker popup on settings page.
Added better string sanitization for input variables.

= 9.3.4 =
Changed the settings page to use Jquery UI Tabs instead of my custom code.
Cleaned up some of the CSS.

= 9.3.3 =
Added code to prevent the recreate_plugin_order function from saving active plugins if the array does not contain the same number of plugins as when it was called.
Added a filter call to remove the active_plugins filters before any plugins are loaded.

= 9.3.2 =
Fixed bug where an error is thrown if the load order has not already been set in the database.

= 9.3.1 =
Moved the function call to maintain the load order to the init function.
Added functionality to insert a newly activated plugin into the load order earlier.

= 9.3 =
Added a function to remove the active_plugins and active_sitewide_plugins filters after plugins are loaded to prevent other plugins from saving a bad list of plugins to the database.
Plugins can now be disabled on the update-core and plugins admin pages without deactivating them.
Changed the priority of the active_plugins and active_sitewide_plugins filters to 1 so they will load before anything else.
Changed the way new plugins are added to the load order after being activated so they are closer to where they would be normally and not always added to the front.
Fixed a bug where the role cookies are not created or deleted on login/logout if Plugin Organizer has been disabled.

= 9.2.6 =
Changed various option names in the database to prevent WP Spamshield from disabling Plugin Organizer
Adding a warning about WP Spamshields malicious behavior.
Changed the way roles where a plugin has been disabled as well as plugin members are displayed in the Plugin Organizer meta box.
Fixed a bug in the SQL like statements used by the plugin search on the PO settings page introduced with a change made in wordpress 4.8.3.

= 9.2.5 =
Adding admin notices to warn users of what could happen when using Plugin Organizer.

= 9.2.4 =
Removing code that deactivates WP-Spamshield as it is pointless to keep releasing countermeasures to prevent their malicious code.

= 9.2.3 =
Added code to prevent a malicious plugin from disabling Plugin Organizer by deactivating it at load time.

= 9.2.2 =
Fixed a bug with the gettext hook being called mutiple times to change the page title on a group view.
Added code to prevent other plugins from altering posted data.

= 9.2.1 =
Set the tolerance of the droppable elements on the right side of the plugin organizer meta box to pointer so the drag elements aren't dropped in the wrong place.

= 9.2 =
Added functionality to move multiple plugins while disabling.
Fixed conflict with plugins setting the z-index of the ui-dialog popup.
Fixed problem with wp_login action hook only sending one argument in some circumstances.

= 9.1.4 =
Changed the post_type varchar length back to 20 in last version which causied a problem with custom post type page.  Changed the size to 50 to allow for longer post_types.

= 9.1.3 =
Changing database statements to modify post_type and user_role to the new sizes for existing installs.

= 9.1.2 =
Changed the length of 2 fields in the po_plugins database table.  The index on these fields was causing problems with some collation settings.

= 9.1.1 =
Missed 2 files in release 9.1 so the plugin search tool always returned no results.  Releasing the missing file changes.

= 9.1 =
Fixed a problem with disabled roles not being displayed on post type page.
Added a tool to search the datbase to see where a plugin is disabled.

= 9.0.6 =
Fixed problem with post_type column in po_plugins table being limited to 20 characters and causing an uncaught database error.
Removed a console.log dbug statement from PT plugins page.

= 9.0.5 =
Fixed SQL error in the find_duplicate_permalinks function.

= 9.0.4 =
Fixed php notice from stored post types array not being set on activation.
Fixed php notice from HTTP_USER_AGENT not being set on in the server array.
Fixed javascript error from role support help icon that prevented the pop up from working.
Put red and blue icons back for users who haven't enabled disable by role.

= 9.0.3 =
Fixed query in MU plugin for affect children.  Removed quotes around column name that were causing the query to fail.

= 9.0.2 =
Fixed problem with query that selects the base settings for a post in the post metabox.
Fixed a problem where logged in users where being given the logged out user set of plugins.

= 9.0.1 =
Fixed PHP warning when array of enabled roles wasn't set on activation

= 9.0 =
Added ability to disable plugins by logged in status and role.
Changed the look of all jquery UI pop ups.
Changed the loading spinner to use fontawesome spinner.

= 8.1 =
Fixing logic that finds parent and wildcard permalinks in the database so a bad query isn't sent if there are no hashes in the where statement.
Fixing logic that finds parent and wildcard permalinks in the database so all matches are pulled instead of just the first.  That way a loop is run on the results as before to weed out any empty entries in the database.

= 8.0 =
Changed the way posts are found in the database at load time to only use one query for fuzzy matching.
Added the ability to have multiple permalinks assigned to one plugin filter.
Fixed the function that finds parent plugins.
Added the ability to use a wildcard in plugin filter permalinks.
Fixed the post type plugins page so it doesn't timeout when a large amount of posts are being updated.
Added ability to set the priority of post types.
Added the ability to set the priority of plugin filters.
Updated screenshots.

= 7.3 =
Added code to hide the disabled mobile list if mobile is not enabled.
Added ability to select plugins and groups from the available list and move those selected to the disabled lists by clicking a button.

= 7.2 =
Added visual indicators to the available items list to show if a plugin or group is disabled.
Fixed ordering of disabled items when all items are added to the disabled lists.
Fixed disabled lists so they don't collapse when clicking to drag an item.

= 7.1 =
Replaced thickbox alerts with jQuery UI Notices to make them mobile friendly.
Fixed group container expansion issue on group and order plugins page.
Created functionality to hide/show disabled plugin lists.

= 7.0.1 =
Adding message to the PO meta box to drag and drop plugins and groups to disable them.

= 7.0 =
New interface for disabling plugins using jquery ui draggable/droppable.
Added color customization for all plugin lists.
Changed the override post type settings checkbox to show the plugin settings for the post being viewed when the checkbox is changed.  Rather than having to save the post first.

= 6.0.11 =
Added functionality to keep the settings on a post/page/post type when the post type settings have been overridden for the first time.
Added functionality to update the permalink in the po_plugins table when the post status is updated.

= 6.0.10 =
Changed function that determines absolute path to use the DIRECTORY_SEPARATOR constant.

= 6.0.9 =
Removed use of WP_PLUGIN_DIR constant and replaced with a custom function to determine plugin directory.

= 6.0.8 =
Removed plugin order check from activation function because it seems to be causing problems for some users.

= 6.0.7 =
Fixing database table name check to not correct uppercase table name when OS ignores case.

= 6.0.6 =
Updating uninstall.php file with new table and option names from the last update.

= 6.0.5 =
Fixed problem where plugins were not removed from groups when plugin was uninstalled.
Fixed database name.  Removed capital letters since it was causing issues with older versions of MySQL.

= 6.0.4 =
Fixed issue with missing css and javascript on certain custom post types.
Fixed issue with saving post type plugins.  An error was encountered some times when saving the plugins.
Added code to ensure the sql indexes exist to improve query times.

= 6.0.3 =
Removed short tags from 3 template files.
Changed check to make sure $ajaxSaveFunction is set in postMetabox.php.

= 6.0.2 =
Fixed display of plugin groups on the plugins page.
Changed group and order js to use anonymous function sent to slideup instead of settimeout.

= 6.0.1 =
Fixed undefined variable warning on multisite activation.
Added check to prevent save buttons from appearing in post metabox on post edit screen.

= 6.0 =
Added ability to set plugins for all posts matching a post type.
Moved the plugin ordering and grouping to it's own page.
Changed the interface to make it more user friendly.
Added uninstall.php to remove all data from the database when the plugin is deleted through the admin.
Fixed ordering of network activated plugins.  They are now displayed on the ordering page at the beginning of the list where they are loaded and can be reordered seperately.
Added functionality to change the color of on/off buttons and rows on the ordering page.
Cleaned up old code.
Changed icons to use Font Awesome and the built in Dashicons.

= 5.7.6 =
Fixed a typo that prevented globally disabled mobile groups from being enabled on a post or page.
Streamlined plugin matching functionality when saving enabled/disabled during meta box save so it all uses a single function instead of multiple if statements.
Fixed the MU plugin so PO can't be disabled on the admin side which locks the user out of all plugin organizer settings.

= 5.7.5 =
Fixed problem with wordpress not deleting rows from the PO_plugins table upon auto emptying trash.
Fixed problem where plugin filters would show up as duplicate permalinks when the plugin filter was in the trash.

= 5.7.4 =
Fixed error on plugins.php when using a ' in plugin group name.
Fixed problem in mobile user agent strings box where a blank line was added on every save.
Added functionality to create a default user agent search string.
Fixed problem correcting ending slash in plugin filter permalink when the permalink is the base url.  Should always have a trailing slash unless it is a subsite of network.

= 5.7.3 =
Restricted search functionality to front end searches.

= 5.7.2 =
Added functionality to find duplicate plugin filters and display a warning on the edit screen.
Fixed search for parent permalinks.  Was stopping the search even if there were no plugins and a parent was found.
Fixed admin url links in error messages.
Fixed plugin group links on the plugins page.

= 5.7.1 =
Fixed queries in PluginOrganizerMU.class.php to properly use enabled post types.
Fixed check for secure protocol in PluginOrganizerMU.class.php

= 5.7 =
Added ability to target the search page.
Added ability to remove all settings from a post/page
Fixed some undefined variable notices
Added organization features for plugin filters using the plugin filter groups.  Can now view all plugins in a group and sort the list by group and permalink.

= 5.6.6 =
Fixed plugin filter permalink slash correction for admin urls.  The admin url should not be corrected since it doesn't rely on permalink structure.
Changed PO meta box code to be normal priority instead of high priority.  Having high priority caused problems with a woo theme and there was no reason to have it as high priority.

= 5.6.5 =
Corrected version check that disabled selective plugin loading from version 5.6.4

= 5.6.4 =
Fixed undefined variable notices.
Fixed problem with multisite where the url was shortened when fuzzy url matching was enabled and the active_plugins option was retrieved.

= 5.6.3 =
Fixed bug where plugin filters lost their settings because they saw themselves as a parent.

= 5.6.2 =
Added delimiter to preg_quote

= 5.6.1 =
Changed array creation to not use shorthand as that created problems for some users.

= 5.6 = 
Removed a print_r statement that had been left in the code from testing.

= 5.5 =
Fixed admin menu item order and default page under Plugin Organizer.
Code cleanup.  $wpdb was globalized in several function but no longer used.
Fixed a problem with trailing slash correction for files.
Fixed a problem with MU plugin not correctly applying to admin files.
Changed jQuery functionality to submit data more efficiently.  No longer has to reset the form data on every submission.
Added code to retrieve the plugins from a parent so that you can see if a parent is affecting a post and what plugins it is disabling on the edit screen.
Removed the check to see if selective plugin loading is enabled before adding the meta box.  Now you will just recieve an error if you have selective plugin loading disabled.

= 5.4 =
Changed the function used from strpos to stripos for mobile browser string matching.
Fixed an issue where site freezes during upgrade.
Changed from using HTTP_HOST to the wordpress url for trailing slash correction.

= 5.3 =
Added css class for network activated plugins on the plugins page.
Moved all of the menus under the Plugin Organizer menu item.
Fixed bug where a trailing slash is added to the permalink when it is referencing a file.
Added the admin css file to the plugins admin page.

= 5.2 =
Added ability to edit the plugin group names.

= 5.1.1 =
Added javascript refresh to the plugins page when you create/edit/delete a group.

= 5.1 =
Added ability to fix permalinks for plugin filters through the settings page.
Created new on of images.

= 5.0.3 =
Fixed issue with group views on the plugins page.

= 5.0.2 =
Moved function call to correct old group members from the init call to the admin_menu action.

= 5.0.1 =
Moved function call to correct old group members from the activation function to the init call.

= 5.0 =
Added ability to use plugin groups to disable/enable plugins.
Added taxonomy to group plugin filters.
Fixed a problem with plugin filter permalinks not having the ending slash if the permalink structure uses it.
Cleaned up old code.

= 4.1.1 =
Fixed bug where no users could reorder plugins if site was not a multisite install.

= 4.1 =
Fixed bug where the permalink for a plugin filter was not saved if no plugins were selected.
Fixed some formatting issues on the plugins page.
Fixed the missing icons on the admin pages that happened with WP 3.8.
Added functionality to only allow network admins access to changing the plugin load order on multisite installs.

= 4.0.2 =
Fixed bug where the plugin load order was not displayed correctly on the page after activating a new plugin.
Fixed an undefined variable warning on line 986 of PluginOrganizer.class.php

= 4.0.1 =
Fixed an issue where a network activated plugin wasn't added to the plugin page if it is set to load first.
Changed the jquery on plugins.php to use the proper id for a plugin row.  Some plugin names differ from their slug.
Fixed an issue where a plugin would be added to the active list multiple times if it was network activated and first in the load order.

= 4.0 =
Moved the storage of the permalink and plugin lists to a custom table to fix an issue with http://core.trac.wordpress.org/ticket/25690.  
Added the use of an md5 hash on permalinks to allow effective indexing and searching using the index.

= 3.2.6 =
Fixed an issue where active_sitewide_plugins is sometimes set to an empty array even though the site is not multisite enabled.  This caused a 0 to be appended to the active plugins array and an error message to appear.

= 3.2.5 =
Fixed an issue where the MU plugin would only allow one plugin to be activated during bulk activation.

= 3.2.4 =
Added functionality to delete all the options that PO creates upon deactivation.  
Added functionality to delete all custom post types created by PO upon deactivation.

= 3.2.3 =
Removed function that deleted the plugin arrays for a post when custom DB's were used. left over from old code.

= 3.2.2 =
Fixed missing post type checkboxes on settings page when saved with nothing selected.

= 3.2.1 =
Removed hard coded table prefix and added the correct base_prefix variable in PluginOrganizer class.

= 3.2 =
Adding the ability to change the order of network activated plugins.
Adding a field to set the name of a plugin filter instead of just using the permalink.
Fixed logic in MU plugin that would stop it from looking if a post was found with an empty array of disabled plugins.

= 3.1.1 =
Adding cache variable to store the plugin list so it is only created once per page load instead of every time the active_plugins option is retrieved.

= 3.1 =
Adding the ability to target specific browsers.  Useful for loading specific plugins for mobile browsers.

= 3.0.10 =
Fixing warning from searching empty array in group members on plugins page.

= 3.0.9 =
Fixing typo in version number check on initialization.
Got rid of code to fix old custom permalink field

= 3.0.8 =
Removed a call to wp_count_posts in the activation function.  It may have been causing issues on activation.

= 3.0.7 =
Removed a call to get_permalink in the activation function.  It may have been causing issues on multisite activation.

= 3.0.6 =
Fixed an issue with activation where too many posts on the site caused the php to run out of memory and the activation to fail.

= 3.0.5 =
Fixed issue on multisite where the $GLOBALS['wp_taxonomies'] array hadn't been created yet so a php warning was thrown.

= 3.0.4 =
Fixed a typo that caused imported filters to not have a permalink.
Added code to repair anyones database that has already been upgraded with bad permalinks.

= 3.0.3 =
Fixed an issue with the advanced meta query from get_posts adding % characters and escaping my % character.

= 3.0.2 =
Fixed an issue when using ignore protocol the first query wouldn't match.
Fixed an issue where a post is found on the first query but no plugins have been disabled so the enabled plugins are overlooked.

= 3.0.1 =
Fixed a problem with fuzzy url matching.  " characters were being added to the url so it would never match.
Commented out the code that deleted the tables and added an option to the databse to prevent multiple imports.  Will add the delete code in a later version to clean up the tables after everyone is stable and has imported their settings.
Added code to ensure that the old MU plugin is deleted before attempting to copy it from the lib directory.

= 3.0 =
Complete redesign of the plugin.
Removed all custom db tables and moved the data to the post_meta table.
Added custom post type plugin_filter to replace the URl admin.
Added custom post type plugin_group to replace the plugin groups table.
The plugins displayed on post/pages/custom post types/global plugins page are now sorted and colored similar to the main plugin page.
There is no longer an enabled and disabled plugin box.  Enabled and disabled plugins are now all managed together to avoid confusion.
Fixed a bug where the MU plugin chopped the url before checking it so it looped 15 times on the homepage before stopping the search for a fuzzy url.
Fixed a bug where globally disabled plugins were listed as inactive when the list of active plugins was accessed.

= 2.6.3 =
Fixing bug that allows plugins to be disabled on the update pages.

= 2.6.2 =
Fixing PHP notices

= 2.6.1 =
Fixing bad characters added during commit

= 2.6 =
Fixed error on windows when inserting into po_post_plugins without specifying all fields.
Added ability to effect children of posts, pages, custom post types.
Redesign of the post edit screen meta box.

= 2.5.9 =
Missed a file when committing 2.5.8.

= 2.5.8 =
Fixing grouping issues.  
Plugin names were not being escaped when building the group list for display so they werent showing up.
On the recently active screen the plugin organizer actions were duplicated and so when adding to group the group name was duplicated.

= 2.5.7 =
Fixing more bad characters being added by svn or wordpress.org.

= 2.5.6 =
Replacing Icons because they were released under creative commons and not gpl.

= 2.5.5 =
Fixing missing db table error message when the table exists on windows server.

= 2.5.4 =
Fixing bad characters being added by svn or wordpress.org.

= 2.5.3 =
Fixed a jquery issue with wp 3.5

= 2.5.2 =
Added warnings on settings page if the database tables are missing.
Removed default value for longtext database fields.  Caused issues on windows.

= 2.5.1 =
Fixed a problem with URL admin not saving edited URLs
Changed the first menu item to settings under Plugin Organizer

= 2.5 =
Removed PHP notice errors.
The plugin organizer plugin can no longer be disabled on the admin.
Added better support for multi-site.
The plugin will now correct plugins that are network activated and activated on the local site so they are only network activated.  This fixes an error where more plugins were seen as active than were displayed on the plugins page.
The plugin organizer features will not load on the network admin.
Network activated plugins can now be disabled.

= 2.4 =
Adding ability to ignore arguments to a URL.  You can now enter URLs into the URL admin with arguments so that http://yoururl.com/page/?foo=2&bar=3 will have different plugins loaded than http://yoururl.com/page/?foo=1&bar=4 and http://yoururl.com/page/.
Fixed URL admin so that it checks to make sure the URL was entered into the database before saying it was successful.

= 2.3.3 =
Undoing a change that was done in 2.3.1 to the request uri that removed arguments from the uri.  It is causing some issues for some users.  Will redesign and create a later release to optionally remove the arguments. 

= 2.3.2 =
When the user hadnt set the number of plugins displayed per page it was being defaulted to 20.  Changed it to default to 999.
Set $endChar to an empty string in PluginOrganizerMU.class.php to prevent debug notices.

= 2.3.1 =
Fixed a javascript error on the URL admin page.
Fixed logic for Global plugins where all plugins were disabled none where getting disabled.
Fixed use of REQUEST_URI.  Now it Splits the REQUEST_URI to trim off URL arguments.
Added ability to reset plugin order back to wordpress default.
Renamed some javascript functions and consolidated some of them.

= 2.3 =
Removed the old admin pages.  The plugins can now be managed directly on the plugins page.
Redesigned the settings page to use ajax queries instead of reloading the page to save settings.
Redesigned the URL admin to use ajax to save and edit URL's instead of reloading the page.
Moved most of the javascript out of the main class and into template files.
Added a setting to preserve the plugin data when it is deactivated.  The plugin data including database tables and MU plugin file can now be removed on deactivation.

= 2.2.1 =
Added ability to ignore the protocol when matching the requested URL by checking a checkbox on the settings page.

= 2.2 =
Added Fuzzy URL matching to the arbitrary URL admin.  URLs can now effect their children.
Added nonce checking to URL admin.
Restructured forms on the main settings page.

= 2.1.3 =
Added checks to ensure plugin load order cant be changed when all plugins are not viewable on the page.

= 2.1.2 =
Fixed group view on plugin organizer page when the plugins per page has been set too low or extremely high.
Fixed setting of the show old admin page when either save settings button is clicked.

= 2.1.1 =
Adding option to show the old admin pages.

= 2.1 =
Added better group management to the plugin admin page.
Removed group management pages from the menu.

= 2.0 =
Added drag and drop functionality to the plugin admin page.
Added group links to the top of the plugin admin page that replace the group dropdown.
Added better checking to make sure the plugin load order can only be changed when all plugins are being displayed.

= 1.2.3 =
Fixed URL admin page.  Enabled plugins list wasnt saving on creation.

= 1.2.2 =
Fixed typo in recreate permalinks function.
Centralized the nonce generation so the PluginOrganizer class now holds it.

= 1.2.1 =
Adding license tag to header and replacing global path variables with path variables inside the PluginOrganizer class.

= 1.2 =
Removed a conditional and some whitespace from the main plugin file becasue it may have been causing issues with activation.  
Adding menu and header icons to pretty up the plugin.

= 1.1 =
Added option to settings page so the selective plugin loading can be enabled or disabled for the admin pages.

= 1.0 =
Added ability to disable plugins in the admin using the Arbitrary URL admin page.
Fixed some flow issues and html problems on the PO admin pages.
Properly escaped all queries

= 0.9 =
Added admin area for entering arbitrary URL's to allow plugin management for url's that don't have a post tied to them.
Added some form validation for the admin screens.

= 0.8.3 =
Fixing a bug with globaly disabled plugins not being enabled on individual posts
Fixing bug with version number not updating when plugin is updated.

= 0.8.2 =
Fixing wrong version number on plugins page.
Adding FAQ's

= 0.8.1 =
Added missing tpl/globalPlugins.php file.

= 0.8 =
Adding custom post type support.

= 0.7.3 =
Fixed activation errors when mu-plugins folder is not writable.

= 0.7.2 =
Fixed bug that reordered plugins back to default when plugins were activated or deactivated.
Fixed jQuery loading indicator on plugin admin.
Fixed Bulk Actions on plugin admin

= 0.7.1 =
Removed display of plugin load order functions on plugin admin if the view is paged.  To view load order functions on plugin admin you must display all active plugins on one page.

= 0.7 =
Wordpress 3.1 fixes for jQuery 1.4.4

= 0.6 =
Added functionality to disable plugins globally and selectively enable them for posts and pages.
Added functionality to create the mu-plugins folder and move the MU plugin class when activated.
New databse layout.  Will be created when plugin is activated.

= 0.5 =
Added functionality to selectively disable plugins by post or page.  
There is now a Must Use plugin component that comes with the main plugin.
To enable selective plugin loading you must move the /wp-content/plugins/plugin-organizer/lib/PluginOrganizerMU.class.php file to /wp-content/mu-plugins.
If the mu-plugins directory does not exist you must create it.

= 0.4.1 =
Fixed empty items in plugin list.

= 0.4 =
Added grouping to the plugin admin page.
Improved ajax requests
Added ajax loading image.
Added page to create and organize plugin groups.

= 0.3 =
Added ajax requests to the settings page so both forms now use ajax.
Added nonce checking to the ajax requests.  
Requires user to have activate_plugins capability.

= 0.2 =
Made function to reorder the plugins on plugin admin page in the order they will be loaded.
Redid the sort functions to use PHP's array_multisort.

= 0.1.1 =
improved the ajax requests on the plugin admin page.  

= 0.1 =
Initial version.

== Upgrade Notice ==

= 10.1.10 =
Fixed PHP warning about array offset when the database returns a bad result in MU plugin