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
