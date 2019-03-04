# Drupal solutions

- drupal site:mode dev
- drush cr //clear all cache
- drush pm:uninstall <module>

**Show Errors**
- add strings to settings.php:
  - error_reporting(E_ALL);
  - ini_set('display_errors', TRUE);
  - ini_set('display_startup_errors', TRUE);

**Export / Import Settings**
- drush config-export --destination <folder>
- drush config-import --source <folder>

**Export / Import database**
- drush sql-dump > ~/my-sql-dump-file-name.sql //export
- drush sql-cli < ~/my-sql-dump-file-name.sql //import


**Drush**
- cd /usr/local
- sudo git clone https://github.com/drush-ops/drush
- cd drush
- sudo composer update
- php drush --version
- sudo rm -f /usr/local/bin/drush
- sudo ln -s /usr/local/drush/drush /usr/local/bin/drush
- drush --version
- https://github.com/drush-ops/drush

**Devel**
- composer require drupal/devel, then go to Extend and install:
- Devel
- Devel generate
- Devel kint
- Web Profiler

**Webform**
- composer require drupal/webform

**Custom theme**
- **create** skeleton folders and files, required for custom theme
- sites/all/themes/mytheme/mytheme.info.yml (name, description, regions)
- sites/all/themes/mytheme/mytheme.libraries.yml (connect css, js)
  - sites/all/themes/mytheme/assets/css
  - sites/all/themes/mytheme/assets/js
- sites/all/themes/mytheme/mytheme.theme (Implements hooks)
- sites/all/themes/mytheme/config/install/mytheme.settings.yml (schemas: [])
- sites/all/themes/mytheme/config/schema/mytheme.schema.yml (two settings)
**templates**
(copy from core/modules/system/templates)
- sites/all/themes/mytheme/templates/html.html.twig
- and any templates, what you need
**Then install your's theme and set is as default**

**Basic settings for great work**
- in /sites/default/settings.php uncomment the lines at the bottom of 'sites/example.com/settings.php'
- in /sites/default/settings.local.php uncomment next strings:
  - $settings['cache']['bins']['render'] = 'cache.backend.null';
  - $settings['cache']['bins']['page'] = 'cache.backend.null';
  - $settings['cache']['bins']['dynamic_page_cache'] = 'cache.backend.null';
- in /sites/default/services.yml set in section twig.config:
  - debug: true
  - auto_reload: true
  - cache: null
- in render.config section:
  - http.response.debug_cacheability_headers: true

**Drupal 8 structure:**
- /core - All files provided by core, that doesn't have an explicit reason to be in the / directory. More details futher down.
- /libraries - 3rd party libraries, eg. a wysiwyg editor. Not included by core, but common enough to warrant inclusion here.
- /modules - The directory into which all custom and contrib modules go.
  - Splitting this up into the sub-directories contrib and custom can make it easier to keep track of the modules. enough to warrant mention here.
- /profile - contributed and custom profiles.
- /themes - contributed and custom (sub)themes
- sites/[domain OR default]/{modules,themes} - Site specific modules and themes can be moved into these directories to avoid them showing up on every site.
- sites/[domain OR default]/files - Site specific files tend to go here. This could be files uploaded by users, such as images, but also includes the configuration, active as well as staged config. The configuration is read and written by Drupal, and should have the minimal amount of privileges required for the webserver, and the only the webserver, to read and modify them.
- /vendor - Backend libraries that Drupal Core depends on. (Symfony, Twig, etc)

*Core directory:*
- /core/assets - Various external libraries used by Core. jQuery, underscore, modernizer etc.
- /core/misc - Frontend code that Drupal Core depends on.
- /core/includes - Functionality that is to low level to be modular. Such as the module system itself.
- /core/lib - Drupal Core classes.
- /core/modules - Drupal Core modules.
- /core/profiles - Drupal Core installation profiles. Minimal, Standard, Testing and Testing multilingual installation profiles by default.
- /core/scripts - Various CLI scripts, mostly used by developers.
- /core/tests - Drupal Core tests.
- /core/themes - Drupal Core themes.
