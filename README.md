Drupal2WordPress Plugin 
=======================

WordPress 3.x+ plugin for importing Drupal 7 (works for WordPress 4.x too)

## Features
* WordPress plugin
* Import options
    - Choose from importing terms, content, comments, and/or users
        - comments can only be imported if content is
    - Associate WordPress post types to Drupal node types
* Cleans Drupal aliases
    - Outputs .htaccess rewrite rules for alias changes


## Import Options
* **Content (Drupal nodes)** 
    - You can associate Drupal node types to WordPress post types.
    - All nodes are imported with their original owner user id (if users are imported, otherwise you can choose the user ID to associate all content to), timestamp, published or unpublished state. 
    - With regards to SEO, Drupal's leading 'content/' prefix for any page is removed.
        - Drupal was more forgiving with malformed aliases (slugs), this plugin will clean the alias to a proper slug.
            - These changes are outputted for you to add to your .htaccess file to do proper redirects.
    - Comments on Content (up to 11 levels of threaded comments) [May make the level nesting optional]
        - Only approved comments are imported due to the high level of spam which Drupal sites might endure (in Drupal this means all comments with status 1)
* **Terms**
    - _Categories_ 
        - WordPress requires that any blog post is associated with at least one category, and not just a tag, hence the script will create a default category (you get to decide what it is) and associate all of the content created into that category.
    - _Taxonomies_
* **Users** 
    - Drupal's user id 0 (anonymous) and user id 1 (site admin) are ignored. 
    - User's basic information is migrated, such as username, e-mail and creation date. 
        - **Users are migrated with no password, which means in WordPress that they can't login and must reset their account details (this is due to security reasons).**
    - Adds default user meta

## Important Info

**This should go without saying but make sure to test this script locally before using on a production environment**

* The script will truncate (delete all records) for the options you select. 
    - This means original WordPress content will be lost, if you have any. (This is to keep the content IDs matching for all options)
        - If you want to keep your content, export it using: _Tools_ -> _Export_
        - When Drupal has been imported, you can import your old data by using: _Tools_ -> _Import_
* Install this plugin as any other plugin
    - Once activated, you will find the importer under _Tools_ -> _Import_ -> _Drupal 2 WordPress_


## Todo
- [x] Allow for custom post type association
- [ ] Import media sources
- [ ] Add multi-lingual import option (a site I need to import uses two languages so I have duplicate content as each post has two versions)
- [ ] Add Drupal version selector to allow for 6 and 8 to be added
- [ ] L10n

## Known Issues
- [ ] Page tags seems to have been broken. That or I messed up previously and thought they had tags. I'm looking into this now


This plugin is based off the repo: https://github.com/lirantal/Drupal2WordPress