[![Build Status](https://travis-ci.org/jpSimkins/Drupal2WordPress-Plugin.svg)](https://travis-ci.org/jpSimkins/Drupal2WordPress-Plugin)

Drupal2WordPress Plugin
=======================

This plugin is based off the repo: https://github.com/lirantal/Drupal2WordPress

WordPress 3.x+ plugin for importing Drupal 7 (Works for WordPress 4.x too)

## Features
* WordPress plugin
* Options to import what you need (options will be improved)
* Outputs .htaccess rewrite rules for alias changes


**This script supports the migration of the following items:**
* **Content (Drupal nodes)** - nodes of type "article" are migrated into WordPress as 'post' content type, and any other Drupal node content type is migrated into WordPress as 'page' content type. All nodes are imported with their original owner user id, timestamp, published or unpublished state. With regards to SEO, Drupal's leading 'content/' prefix for any page is removed.
    - Comments on Content (up to 11 levels of threaded comments) - only approved comments are imported due to the high level of spam which Drupal sites might endure (in Drupal this means all comments with status 1)
* **Terms**
    - _Categories_ - WordPress requires that any blog post is associated with at least one category, and not just a tag, hence the script will create a default category (you get to decide what it is) and associate all of the content created into that category.
    - _Taxonomies_
* **Users** - Drupal's user id 0 (anonymous) and user id 1 (site admin) are ignored. User's basic information is migrated, such as username, e-mail and creation date. Users are migrated with no password, which means in WordPress that they can't login and must reset their account details (this is due to security reasons).
    - Adds default user meta too

## Important Info

* The script will truncate (delete all records) for the options you select. 
    - This means content will be lost if you already have some
    - This is to keep the IDs matching properly
* Install the plugin as any other plugin
    - Once activated, you will see the plugin under _Tools_ -> _Drupal2WordPress_


## Todo
- [ ] Import media sources
- [ ] Allow for custom post type association
- [ ] L10n
- [ ] Add Drupal version selector to allow for 6 and 8 to be added