# Demo how to upgrade Drupal 8 to 9 #

Upgrading Drupal 8 to 9 using Composer is a more efficient and streamlined process. Here's how to do it:

1. Backup your Drupal 8 site: It's essential to back up your Drupal 8 site and database before proceeding with the upgrade. This ensures that you can easily restore your site if anything goes wrong during the upgrade process.

2. Ensure your site meets the system requirements for Drupal 9, including PHP 7.3 or higher and Drupal 8.8 or higher.

    ![Drupal 8 status](/images/drupal8-status.png)

3. Next need to install **upgrade_status** module.
```
composer require drupal/upgrade_status
drush en upgrade_status
drush cr
```
4. Goto this location **/admin/reports/upgrade-status**. It will show compatibility of Drupal 9.

   ![Drupal upgrade](/images/D9-upgrade-status.png)
   ![Drupal upgrade](/images/D9-upgrade-status1.png)

5. You can run below command to check outdated project.

   **composer outdated drupal/***
   
   ![Composer outdated](/images/composer-outdated-project.png)
   
6. Execute the following command to update Drupal

   **composer require drupal/core-recommended:^9.5.3 drupal/core-composer-scaffold:^9.5.3  drupal/core:^9.5.3 drupal/core-dev:^9.5.3 --update-with-all-dependencies**
   
   #### Note: In the composer.json file, you can check for the "drupal/core" package and any packages that start with "drupal/core-" to determine which packages need to be updated. ####
   
   ![Drupal core pattern](/images/composer-json-updated.png)
   
7. If you encounter a **require dependencies** error when running the command mentioned earlier, you will need to add each dependency individually using the **composer require** command. For example, if you receive an error message indicating that the Drupal contrib module **"drupal/front" is not satisfiable**, you can navigate to the Drupal contrib "front" project page and install a Drupal 9 compatible version of "drupal/front" using the following command.

   **composer require 'drupal/front:9.1.x-dev@dev'**
   
   ![Drupal front](/images/composer-outdated-front.png)
   
   **Note: If you encounter compatibility issues with other contrib modules, you will need to follow the same process and install Drupal 9 compatible versions of those modules using the appropriate composer require command.**
   
8. Next, you should rerun the command for step number 6. However, if you encounter another issue, such as a problem with the Symfony package, please refer to the following screenshot for more information.

   ![Symfony service contract](/images/composer-outdated-symfony-translation.png)
   
     To resolve the issue with the missing Symfony package, you can add it to the **composer require** command along with the other necessary Drupal 9 compatible packages. Here is an example command that includes the necessary packages:
   
   **composer require drupal/core-recommended:^9.5.3 drupal/core-composer-scaffold:^9.5.3 drupal/core:^9.5.3 drupal/core-dev:^9.5.3 drupal/devel symfony/service-contracts --update-with-all-dependencies**

    Please note that certain Symfony packages may require a specific version, and in such cases, you should include the required version in the **composer require** command. Here's an example command that includes the necessary packages and specific Symfony package version: 

   **composer require drupal/core-recommended:^9.5.3 drupal/core-composer-scaffold:^9.5.3 drupal/core:^9.5.3 drupal/core-dev:^9.5.3 drupal/devel symfony/service-contracts symfony/cache symfony/process:^4.4 --update-with-all-dependencies**
   
   ![Symfony process outdated](/images/composer-outdated-process.png)

  Note: You can use **composer why** to check dependency of package For example, if you run **composer why symfony/process**, Composer will show you the list of packages that required symfony/process, along with their versions. This information can help you to understand the dependency tree of your project and identify which packages are necessary for your project to function correctly.
  
9. Your final command to update Drupal with the necessary dependencies would be: 

    **composer require drupal/core-recommended:^9.5.3 drupal/core-composer-scaffold:^9.5.3 drupal/core:^9.5.3 drupal/core-dev:^9.5.3 drupal/devel symfony/service-contracts symfony/cache symfony/process:^4.4 --update-with-all-dependencies**
    
    ![Successfull installed](/images/successfull-install.png)

10. After updating your Composer dependencies to Drupal 9, you need to run the update script to update your database. To do this, run the following command in the root directory of your drupal project.

    **drush updb**
    
   Or You can run **update.php**, you need to log in as an administrator and navigate to yoursite.com/update.php in your web browser. This will trigger the update script to run and display a progress bar showing the status of the updates being applied. Once the updates have been completed, you will be redirected back to the site's home page.

11. Once you have updated the Drupal core and its dependencies, you can run the **composer require** command to update any outdated Drupal contrib projects. To check which Drupal contrib projects are outdated, you can run the **composer outdated** command. In your specific project, you found the following contrib projects were outdated, so you ran the following command to update them:

    **composer require drupal/address drupal/admin_toolbar drupal/autologout drupal/bootstrap_barrio drupal/bootstrap_sass drupal/devel_php drupal/entity_reference_revisions drupal/externalauth drupal/google_analytics drupal/imageapi_optimize drupal/json_field drupal/mailsystem drupal/paragraphs drupal/redis drupal/token**
   
       ### Note: If any patches are required for the drupal core, contrib modules or themes that you are updating, you will need to create or find the patch and add it to the composer.json file. On the other hand, if you cannot find a Drupal 9 compatible version of a contrib module or theme that you need, you will need to create or convert it to make it compatible with Drupal 9. ###
   
12. After updating the Drupal core and its dependencies, you will need to update any custom modules and themes that you have. You can use the **Drupal Check library to check for any deprecated code** and then **remove it using the Drupal Rector library** or manually remove the deprecated code.
 
    ![Drupal9](/images/drupal9.png)
    ![Drush status](/images/drush-staus-d9.png)
    
    :house: [Home Page](README.md) | [<< Previous Page](drupal-8-to-9-upgrade.md)
