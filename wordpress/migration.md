# Wordpress Migration

## A simple guide to migrate local project on demo/client side

1. download the all-in-one-wp-migration-premium.zip
2. install the plugin via the wordpress admin interface and activate the plugin
3. go in to plugin and export site as file
4. create a new site on demo/client side, follow step 1,2 do install and activate the migration plugin
5. now it's time upload backup file onto the new site. It is recommended to upload via file manager instead of the plugin interface. The backup folder should be located as `<root>/wp-content/ai1wm-backups`. upload the backup file into the folder
6. you should see the backup in the backup page in migration plugin interface, hit the restore button
7. now the new site should be fully migrated

### NOTE:
- avoid subdomain such as `domain.com/site`, use `site.domain.com` instead, otherwise a lot of links will be broken and it's annoying to manually fix them
- make sure .htaccess set up correct, use template below
```xml
# BEGIN WordPress
# The directives (lines) between "BEGIN WordPress" and "END WordPress" are
# dynamically generated, and should only be modified via WordPress filters.
# Any changes to the directives between these markers will be overwritten.
<IfModule mod_rewrite.c>
    RewriteEngine On
    RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]
    RewriteBase /
    RewriteRule ^index\.php$ - [L]
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteRule . /index.php [L]
</IfModule>
# END WordPress
```