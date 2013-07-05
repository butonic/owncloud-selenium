*As a developer I want to be able to click a button in Firefox and have it test the core owncloud functionality.*

Requirements
------------

Go to http://docs.seleniumhq.org/projects/ide/ and download the Selenium IDE for firefox. Version 2.1.0 should be fine with FF 22/23.

Checkout this repository anywhere on your machine.

Configuration
-------------

The ownCloud test suite is saved in owncloud.html. Open it in  the selenium IDE and select the setup test case. The tests need to upload several files from the official owncloud demo/test data, so replace `/replace/with/path/to/demodata/folder` with the path to a checked out version of https://github.com/owncloud/test-data

Current status
--------------

Already implemented:

- logout
- login failure warning
- login with admin user
- create test user with cryptic password
- check and close welcome dialog
- file upload
- multiple file upload
- file upload autorename

Next steps
----------

I'll try to add whatever we can automate from https://github.com/owncloud/core/wiki/Testplan with priority for file related actions and sharing. Any help is welcome.

Future
------

Currently only works in Firefox / the Selenium IDE. But the script can be executed to use it with the selenium webdrivers.

Automated testing FTW!
