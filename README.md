*As a developer I want to be able to click a button in Firefox and have it test the core owncloud functionality.*

Requirements
------------

Go to http://docs.seleniumhq.org/projects/ide/ and download the Selenium IDE for firefox. Version 2.1.0 should be fine with FF 22/23.

Checkout this repository anywhere on your machine.

Configuration
-------------

The ownCloud test suite is saved in owncloud.html. Open it in  the selenium IDE and select the setup test case. The tests need to upload several files from the official owncloud demo/test data, so replace `/replace/with/path/to/demodata/folder` with the path to a checked out version of https://github.com/owncloud/test-data

Smoke Test with ownCloud7 Server
--------------------------------

This example logs in the admin user through a simple Selenium test case.
It may fail in various ways, see below for some possible outcomes and how to fix them.

  git clone git@github.com:owncloud/core.git
  sudo rm -f core/config/config.php

* ... and get apache up with master ... if not already running.
* Create the admin user with password admin 
* Finish setup with SQLite

  git clone https://github.com/butonic/owncloud-selenium.git
  git clone git@github.com:owncloud/test-data.git
  firefox http://docs.seleniumhq.org/download/
  firefox https://addons.mozilla.org/en-US/firefox/addon/stored-variables-viewer-seleni/
  firefox
   -> Tools -> Selenium IDE
     Base URL: http://localhost/core/
   File -> Open... -> owncloud-selenium/owncloud.html
   (click) Setup (in Test Case in left pane)
   (click) dataFolder (in column Value in right pane)
    -> Target: /home/testy/oc/github/test-data/
   File -> Save Test Case (this will overwrite Setup.html)
   (double click) Setup (in left pane 'Test Case')
   Stored-Vars -> Refresh	(just to verify the vars are there)
     (Find in Page) admin
   (double click) Login Admin success
   Actions -> Play current test case

* [error] Element css=#body-login not found

  then the webpage http://localhost/core/index.php?logout=true probably displays

   {"data":{"message":"Token expired. Please reload page."},"status":"error"}

  Log out using the drop down at the right hand side from your user name. 
  then play the test case again.
  The url parameter ?logout=true does not work without a requesttoken. TBD

* Success: User admin is now logged in and you see the Files app.



Current status
--------------

Already implemented:

- [X] logout
- [X] login failure warning
- [X] login with admin user
- [X] create test user with cryptic password
- [X] check and close welcome dialog
- [X] file upload
- [X] multiple file upload
- [X] file upload autorename
- [X] file rename
- [X] sharing file with groups
  - [ ] check read only permission
  - [ ] check read & write permission
  - [ ] check read, write and reshare permission
- [ ] sharing folder with groups
  - [ ] check read only permission
  - [ ] check read & write permission
  - [ ] check read, write and reshare permission
- [ ] sharing file with public link
  - [ ] check read only permission
- [ ] sharing file with public link
  - [ ] check read only permission
  - [ ] check read & write permission
...

Next steps
----------

I'll try to add whatever we can automate from https://github.com/owncloud/core/wiki/Testplan with priority for file related actions and sharing. Any help is welcome.

Future
------

Currently only works in Firefox / the Selenium IDE. But the script can be executed to use it with the selenium webdrivers.

Automated testing FTW!
