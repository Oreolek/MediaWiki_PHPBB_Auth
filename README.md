MediaWiki_PHPBB_Auth
====================

This extension links MediaWiki to phpBB's user table for authentication, and disallows the creation of new accounts in MediaWiki. Users must then log in to the wiki with their phpBB account.

MediaWiki Page: http://www.mediawiki.org/wiki/Extension:PHPBB/Users_Integration

REQUIREMENTS
=================

* PHP5
* MySQL 5
* MediaWiki 1.26.0+ 
* phpBB 3.2

INSTALL:
=================

Create a group in PHPBB for your wiki users. I named mine "Wiki". 
You will need to put the name you choose in the code below. 

NOTE: In order for a user to be able to use the wiki they will need to 
be a member of the group you made in the step above.

Copy this folder into /extensions/ as `Auth_phpBB` so that it would be under `/extensions/Auth_phpBB`

Open LocalSettings.php. Put this at the bottom of the file. Edit as needed.

```php
// PHPBB User Database Plugin. (Requires MySQL Database)
wfLoadExtension('Auth_phpBB');

// Setting this to true causes the mediawiki usernames
// to match the casing of the phpbb ones (except with
// the first letter set uppercase.)
// Setting this to false causes usernames to be all
// lowercase except for the first character.
$wgAuth_Config_useCanonicalCase = false;

// Name of your PHPBB group users need to be a member of to use the wiki. (i.e. wiki)
// This can also be set to an array of group names to use more then one.
$wgAuth_Config_wikiGroup = "Wiki";

// This tells the Plugin to require a user to be a member of the above
// phpBB group. (ie. wiki) Setting this to false will let any phpBB
// user edit the wiki.
$wgAuth_Config_useWikiGroup = false;

// false if the same as MediaWiki DB host, user, password and database.
$wgAuth_Config_mysqlHost = false;
$wgAuth_Config_mysqlUser = false;
$wgAuth_Config_mysqlPassword = false;
$wgAuth_Config_mysqlDatabase = false;

// Name of your PHPBB user table. (i.e. phpbb_users)
$wgAuth_Config_userTable = 'phpbb3_users';

// Name of your PHPBB groups table. (i.e. phpbb_groups)
$wgAuth_Config_groupTable = 'phpbb3_groups';

// Name of your PHPBB user_group table. (i.e. phpbb_user_group)
$wgAuth_Config_userGroupTable = 'phpbb3_user_group';

// Path from this file to your phpBB install.
$wgAuth_Config_phpBBPath = '../forum/';
```
