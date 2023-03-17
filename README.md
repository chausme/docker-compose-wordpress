# docker-compose-wordpress

🐳 Very simple Docker Compose workflow for local WordPress development on Windows with WSL2

## Overview

### Sites

This setup is intended for subdirectory-based development as per below, however could work for multiple separate projects with some adjustments

./apps<br />
&ensp;&ensp;&ensp;./site1 - http://wp.local/site1<br />
&ensp;&ensp;&ensp;./site2 - http://wp.local/site2<br />
&ensp;&ensp;&ensp;./site3 - http://wp.local/site3<br />
./database<br />
./logs<br />
./nginx<br />
./php<br />

### PHP

These versions are included:

-   7.4
-   8.1
-   8.2

These extensions are included:

-   MySQLi
-   GD
-   SimpleXML
-   Zip

### Database

MySQL 8 data is stored in persistent storage at `./database`

## Usage

-   Make sure you have Docker Desktop installed and opened
-   Clone this repository inside Linux filesystem
-   Put site subdirectories inside `./apps` in the root of the cloned repo
-   Add `.env` file with variables based on `.env.local`
-   Run `docker-compose build` to build images
-   Run `docker-compose up` to start containers, it will take more time on an initial run
-   Update `Windows\System32\drivers\etc\hosts` file with these two lines:

```
127.0.0.1 wp.local
127.0.0.1 www.wp.local
```

-   Connect to MySQL server with DBeaver or use another approach, create databases and import database dumps as necessary
-   (each site) Update WP config with password, user and host values from `.env` file. _Please note:_ `DB_HOST` should be `database_wp` not `localhost`
-   (each site) Update or set `WP_HOME` and `WP_SITEURL` values inside WP config e.g. `http://wp.local/site1`
-   (each site) Update directory owner to your WSL user and group to `www-data`, e.g. `sudo chown -R alex:www-data site1/`

_Optionally_

-   Create `version.php` or a similar file inside `./apps` with `<?php phpinfo();` which is useful for checking current PHP version and installed extensions
-   Adjust PHP version if necessary inside `.env` file
-   Rebuild `php_wp` container with `docker-compose build php_wp`
-   Restart `php_wp` container with `docker-compose restart php_wp` or stop and start with `docker-compose stop php_wp && docker-compose up php_wp`
-   (each site) In order to upload files from WP dashboard, update owner of `/uploads` directory to `www-data`, some plugins might require other directories update as well

## Will it work somewhere else?

While untested, this setup potentially works on Windows without WSL2, Linux and macOS with little to no changes

Also possible to use on staging server with some nginx tweaking including SSL certificates support. Not intended for production though since php-fpm works much better in that case
