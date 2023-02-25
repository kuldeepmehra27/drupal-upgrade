# Demo how to upgrade Drupal 8 to 9 #

Upgrading Drupal 8 to 9 using Composer is a more efficient and streamlined process. Here's how to do it:

1. Backup your Drupal 8 site: It's essential to back up your Drupal 8 site and database before proceeding with the upgrade. This ensures that you can easily restore your site if anything goes wrong during the upgrade process.

2. Ensure your site meets the system requirements for Drupal 9, including PHP 7.3 or higher and Drupal 8.8 or higher.

3. Next need to install **upgrade_status** module.
```
composer require drupal/upgrade_status
drush en upgrade_status
drush cr
```
4. Goto this location **/admin/reports/upgrade-status**. It will show compatibility of Drupal 9.

5. You can run below command to check outdated project.
   **composer outdated drupal/***
   
6. Now run below command to update drupal.
   **composer require drupal/core-recommended:^9.5.3 drupal/core-composer-scaffold:^9.5.3  drupal/core:^9.5.3 drupal/core-dev:^9.5.3 --update-with-all-dependencies**
   **Note: In composer.json file you can check drupal/core and drupal/core-* that needs to update.
   
7. When you run above commands you will get require dependencies error. So one by one you need to add these dependencies in composer require command. Like this
   I have got contrib module error **drupal/front not satisfiable**. I have goto drupal contrib front project page and installed drupal 9 compatible version of **drupal/front** using below command
   **composer require 'drupal/front:9.1.x-dev@dev'**
   You need to follow same process for others contrib module if you will get compatibility issues.
   
8. Now we need to run step no 6 command again. This time I have got symfony package issue check below ss for more details.

   So I have added that package in my composer require command like below.
   **composer require drupal/core-recommended:^9.5.3 drupal/core-composer-scaffold:^9.5.3  drupal/core:^9.5.3 drupal/core-dev:^9.5.3 drupal/devel symfony/service-contracts --update-with-all-dependencies**

   Some symfony package require specific version. So we need to add that version in composer require command. Check below SS
   composer require drupal/core-recommended:^9.5.3 drupal/core-composer-scaffold:^9.5.3  drupal/core:^9.5.3 drupal/core-dev:^9.5.3 drupal/devel symfony/service-contracts symfony/cache **symfony/process:^4.4** --update-with-all-dependencies

   So this is my final command 
   **composer require drupal/core-recommended:^9.5.3 drupal/core-composer-scaffold:^9.5.3  drupal/core:^9.5.3 drupal/core-dev:^9.5.3 drupal/devel symfony/service-contracts symfony/cache symfony/process:^4.4 --update-with-all-dependencies**


10. Now run **composer require** command to update outdated drupal contrib projects. Run **composer outdated drupal/** this command to check outdate drupal contrib project.
    In my project I have found following contrib project outdated so I have run follow command to update drupal contrib package.
    **composer require drupal/address drupal/admin_toolbar drupal/autologout drupal/bootstrap_barrio drupal/bootstrap_sass  drupal/devel_php drupal/entity_reference_revisions drupal/externalauth drupal/google_analytics drupal/imageapi_optimize drupal/json_field  drupal/mailsystem drupal/paragraphs drupal/redis drupal/token**
   
   ### Note: If any patch require for contrib modules/theme you need to create or find it and add in composer.json file or If you will not found any contrib module or theme drupal 9 compatible you need to create/convert it ###
   Example: 

5. Update contributed modules and themes: Update all contributed modules and themes to their latest versions. Execute following command to update contribe module
  **composer require drupal/json_field drupal/front:^9.1.x-dev drupal/devel:^4.0  drush/drush:^10.0.0 drupal/swiftmailer --update-with-all-dependencies**
