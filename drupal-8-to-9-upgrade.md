## How to upgrade drupal 8 to drupal 9? ##

Upgrading from Drupal 8 to Drupal 9 involves the following steps:

1. **Review your site's modules and themes:** Before starting the upgrade process, you should review your site's modules and themes to ensure that they are compatible with Drupal 9. Any modules or themes that are not compatible will need to be updated or replaced before upgrading. 

2. **Ensure that your Drupal 8 site is up-to-date:** Before upgrading to Drupal 9, you should ensure that your Drupal 8 site is up-to-date with the latest updates and patches.Update to Drupal 8.8.x or 8.9.x

3. **Check the status report:** Go to the Status Report page of your Drupal 8 site (Reports > Status Report) to check for any issues or warnings that may affect the upgrade process. Resolve any issues or warnings that are identified.

4. **Use the Upgrade Status module:** Install and enable the [Upgrade Status module](https://www.drupal.org/project/upgrade_status) on your Drupal 8 site to check the compatibility of your site with Drupal 9 and to identify any issues that may arise during the upgrade process. Follow the instructions provided by the module to address any issues that are identified.

5. **Upgrade to Drupal 9:** Once you have resolved any issues and ensured that your site is compatible with Drupal 9, you can begin the upgrade process. This can be done using the Upgrade Status module, which provides a link to the Drupal 9 upgrade page. [Environment requirements of Drupal 9](https://www.drupal.org/docs/understanding-drupal/how-drupal-9-was-made-and-what-is-included/environment-requirements-of-drupal-9) check this link.

6. **Test your upgraded site:** Once the upgrade process is complete, you should thoroughly test your upgraded site to ensure that all functionality is working as expected.

7. **Update your modules and themes:** After upgrading to Drupal 9, you should update your site's modules and themes to the latest compatible versions.  If we cannot find any contributed module/themes that is compatible with Drupal 9, we will need to convert it into a custom module/themes. Update the custom code remove deprecated codes.

8. **Review your site's settings and configuration:** Review your site's settings and configuration to ensure that they are still appropriate for your site's needs.

That's it! You have now upgraded your Drupal 8 site to Drupal 9.

here is the official link how to [upgrade drupal 8 to 9](https://www.drupal.org/docs/upgrading-drupal/drupal-8-and-higher)


## Tools for upgrading ##

#### Drupal check ####
Drupal Check can scan for use of @deprecated code and suggest a fix, as well as optionally perform static analysis. This makes it easier to locate the parts of your codebase that will need to be updated in order ensure Drupal 9 compatibility.
Follow this [link](https://github.com/mglaman/drupal-check) to intall drupal check.
[Check this](https://mglaman.dev/blog/proper-introduction-drupal-check) for more details.

#### Drupal rector #### 
Drupal Rector is a tool that automates the process of updating Drupal code from one version to another. Follow this [link](https://github.com/palantirnet/drupal-rector) to install drupal rector.

#### Upgrade rector ####
[Upgrade rector](https://www.drupal.org/project/upgrade_rector) module offers automated code fix suggestions to make your modules compatible with Drupal 9.  It only has partial coverage for deprecated APIs. This is for Drupal 8 only and is still a work in progress.
It is important that the 'upgrade reactor' module fixed automatically more than 50% of the updates of the 200 most used modules.




:house: [Home Page](README.md) | [<< Previous Page](README.md) | [Next Page >>](drupal-8-to-9-upgrade-demo.md)


