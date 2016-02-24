# Spark Green Backups Module

## Authors
	* Julian Smith <julian@wubies.org>

## Overview
This module allows Database and Assets backups to be conducted via the CMS, URLs and commandline. 
It allows facilitates the transfer of backups to a target server. 

## Requirements 
	* SilverStripe 3.*

## Installation
composer require spark-green/silverstripe-backup dev-master

## Usage

### Setup
SSH keys must be set up to allow apache user to ssh to target server without password

###  CMS
Backup will appear as a tab in the Settings of the CMS. Here you can set whether you would like it backup the database, assets, or both. You can also choose whether you would like to transer the files via SSH as well as defining the SSH settings for transfer. Remember to save your settings before pressing the 'Back up now' button.

You must also enter up to two IP address from which you would like the task to be called.

### via Commandline
To call the task via commandline, first, change the directory to your webroot using the 'cd' command: 

	'cd /path/to/your/site'

Follow this command with: 

	'sake /BackupTask'.

The task will use the settings set in the CMS by default but you can override these by setting any of three boolean parameters in the command. 

The parameters are 'db', 'assets', and 'ssh'. 'db' and 'assets' defines whether you would like to back up the database and assets. 'ssh' defines whether you would like to transfer the backups to a target server. In this case the SSH settings from _config.php would override the SSH settings from the CMS.  

For example, if you wanted to back up just the database and transfer it to your target server the command would be:
	
	'sake /BackupTask db=true ssh=true'

If you wanted to back up the database and assets but have no transfer take place the command would be:

	'sake /BackupTask db=true assets=true'

If you pass no parameters the CMS Settings will be used

### via URL
Calling the task through the URL is similar to calling through the commandline. 
The URL to call the task will be:

	/your/site/webroot/BackupTask

The URL uses the same parameters as the commandline but in a query string:

	/your/site/webroot/BackupTask?db=true&assets=true&ssh=true

Setting SSH to true when calling the task through the URL will use the default SSH Settings or those set in the _config.php file. 

If you pass no parameters the CMS Settings will be used.

--------------------------------------------------------------------------------

I think that about covers it! If you have any questions contact one of the authors. Probably Dylan. 


