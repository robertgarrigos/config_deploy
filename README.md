Config Deploy
======================

Config Deploy enables you to deploy partial configuration of a site through the
Backdrop GUI in a single upload file. This module is aimed at web builders who
don't want to use git to synchronize the config files of their local site with
staging or production.

Requirements
------------

This module requires that the core's Config Manager module be enabled.

Installation
------------

- Install this module using the official Backdrop CMS instructions at
  https://docs.backdropcms.org/documentation/extend-with-modules.
- Visit the configuration page under Administration > Configuration >
- Development > Configuration >  Deploy (admin/config/development/configuration/
- deploy) and create a new snapshot of the active config dir.

Documentation
-------------

Temporal documentation here is to be moved to the wiki.

How to use this module? Let's assume the following workflow of a sitebuilder to
create a new feature for a client:

1. On the development site, create the feature, whether it is a new content type
with new fields, a new view or a new layout.
1. In order to test the new feature on the staging site, new or modified config
files need to get synchronized with the staging site. This can be done with git
or by uploading each individual configuration file through the Barckdrop's GUI
1. Once tested on staging, new feature can be deployed to production, again with
git or by uploading each individual configuration files.

What is the problem if you don't want or cannot use git? A new content type,
with 12 new fields, a couple of new views and a layout are configured with 30
individual configuration files that would need to be uploaded individually
with the Config Manager. Besides, the user has to know which exact configuration
files have been created or modified to get that specific new feature.

This module aims to facilitate this job by:

1. Listing all the new and modified configuration files since a specific time.
2. Compressing those files ONLY in a deploy.tar.gz file which can be uploaded to
staging or production sites through the Full Import form of the Configuration
Manager, in a single step.

How to accomplish this?

1. Go to the configuration of this module on admin/config/development/configurat
ion/deploy.
1. Create a new snapshot. This will create a copy of the current active config
directory within the private path (which needs to be set).
1. Start creating your new feature. At any time, you can go to the admin page of
this module to see what the new and modified config files are. This is done by
comparing the actual state of the active config directory with the created
snapshot config directory.
1. Whenever you are ready to deploy, click on 'Download deploy file' in the
admin page of this module.
1. Go to the staging site and upload the downloaded deploy.tar.gz file with the
Full Import form of the Configuration Manager (admin/config/development/configur
ation/full)
1. Backdrop will show you the synch page with a list of missing files and all
the new and modified files. You can ignore the missing files BUT remember to
leave unchecked (by default) the new checkbox you will find at the bottom of the
sync form: this will prevent Backdrop to delete all the missing config files
it has found in the deploy.tar.gz file.
1. Click on 'Import all' button to get your new feature deployed in the site.

This module has some limitations, at this time:

1. It only works with configurations in files, not in the DDBB.
1. It is a new module and not fully tested. Please, use it with care. It would
be a very good idea to have a backup of you active config directory if you use
it. You can use the contrib module Backup Migrate for this.

Issues
------

Bugs and feature requests should be reported in [the Issue Queue](https://github.com/backdrop-contrib/foo-project/issues).

Current Maintainers
-------

- [Robert Garrigós](https://github.com/robertgarrigos).

Credits
-------

- Originally written for BAckdrop by [Bob Brown](https://github.com/robertgarrigos).

License
-------

This project is GPL v2 software.
See the LICENSE.txt file in this directory for complete text.

<!-- If your project includes other libraries that are licensed in a way that is
compatible with GPL v2, you can list that here too, for example: `Foo library is
licensed under the MIT license.` -->
