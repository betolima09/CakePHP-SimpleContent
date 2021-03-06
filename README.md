# SimpleContent
- - -

# Intro

This CakePHP plugin makes it possible to simply add, edit and delete content pages. For example, if you created a webshop CakePHP app and need some semi-static pages (the admin can edit) like a terms or contact page, this plugin makes that kind of simple easy editable pages possible without the need of a full CMS.

# Requirements

This plugin requires jQuery to be loaded. It uses CKEditor 4 and the editablediv technique for editing pages.


# Installation and Setup


(1) Check out a copy of the SimpleContent CakePHP plugin from the repository using Git :

git clone http://github.com/stefanvangastel/CakePHP-SimpleContent.git

or download the archive from Github : https://github.com/stefanvangastel/CakePHP-SimpleContent/archive/master.zip

You must place the SimpleContent CakePHP plugin within your CakePHP 2.x app/Plugin directory.

(2) Load the plugin in app/Config/bootstrap.php

// Load SimpleContent plugin, with loading routes for short urls
CakePlugin::load('SimpleContent', array('routes' => true));

(3) Load the database structure SQL file to create the required table in your database or use the cake schema shell.

user@host$ cake schema create --plugin SimpleContent 

or load the SQL struct file in your db from location: app/Plugin/SimpleContent/db/simplecontent_table_structure.sql

(4) Optional configuration

(4.1) Filemanager plugin for CKeditor

To enable the filemanager plugin, copy or symlink the /SimpleContent/webroot/filemanager/ directory to /app/webroot/filemanager
(CakePHP won't allow usage of PHP files from the plugin/webroot dir's)

Configure filemanager (eg. for Auth in filemanager/connectors/php/filemanager.config.php)

(4.2)  Change the layout for the display and edit functions of the plugin.

You can do this in /SimpleContent/Controller/SimpleContentAppController.php

(4.3)  Change the Auth settings for the edit and create functions of the plugin.

You can do this in /SimpleContent/Controller/SimpleContentAppController.php

(5) Visit http://YOUR_URL/sc/

# Tips

If you want to include the content of a certain page, you can use this in the view of that page:

	<?php
	$page = $this->requestAction('/sp/10/Slugged_page_title'); //10 is the id of the page, that is all that matters. The slugged title is nice for Google
	
	if( ! empty($page['SimplePage']['content']) ){
		
		//Title
		echo '<h1>'.$page['SimplePage']['title'].'</h1>';
		
		//Content
		echo $page['SimplePage']['content']; 
	}
	?>

This way you can use the content of pages created by SimpleContent whereever you want.
