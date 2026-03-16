# Docker Compose WordPress

🐳 Simple Docker Compose environment for local WordPress development on Windows with WSL2

## Overview

### Sites

This setup is intended for subdirectory-based development as shown below. It can also be adapted for multiple separate projects with small adjustments.

```
./apps
  ./site1  -> http://wp.local/site1
  ./site2  -> http://wp.local/site2
  ./site3  -> http://wp.local/site3
./database
./logs
./nginx
./php
```

### Dockerfiles

Uses the latest Docker base images. While this may introduce occasional upstream changes, no stability issues have been encountered so far

### PHP

The following PHP versions are available:

- 5.6 (minimal support for legacy projects)
- 7.4
- 8.0
- 8.1
- 8.2
- 8.3
- 8.4
- 8.5

The following extensions are included for most PHP versions:

- MySQLi
- GD
- SimpleXML
- Zip

### Database

MySQL 8 data is stored persistently in the `./database` directory

## Usage

- Make sure Docker Desktop is installed and running
- Clone this repository inside the Linux filesystem (WSL)
- Place site subdirectories inside `./apps` in the root of the repository
- Create a `.env` file using `.env.local` as a reference
- Run `docker compose build` to build the images
- Run `docker compose up` to start the containers (the first run may take longer)
- Update the `Windows\System32\drivers\etc\hosts` file with the following entries:

```
127.0.0.1 wp.local
127.0.0.1 www.wp.local
```

- Connect to the MySQL server using DBeaver or another client, create databases and import dumps as needed
- For each site, update the WordPress config with the database credentials from the `.env` file  
  _Note:_ `DB_HOST` should be `database_wp`, not `localhost`
- For each site, update or set `WP_HOME` and `WP_SITEURL`, for example: `http://wp.local/site1`
- For each site, update the directory owner to your WSL user and group to `www-data`, e.g. `sudo chown -R username:www-data site1/`

_Optional_

- Create a `version.php` (or similar) file inside `./apps` containing `<?php phpinfo();` to check the current PHP version and installed extensions
- Adjust the PHP version in the `.env` file if necessary
- Rebuild the `php_wp` container with `docker compose build php_wp`
- Restart the `php_wp` container with `docker compose stop php_wp && docker compose up php_wp`
- For each site, to enable file uploads from the WordPress dashboard, update the owner of the `/uploads` directory to `www-data`. Some plugins may require additional directories to be updated as well

## Will it work somewhere else?

While untested, this setup should also work on Windows without WSL2, Linux, and macOS with little or no changes

It may also be possible to use it on a staging server with some nginx adjustments, including SSL certificate support.  
However, it's not intended for production use, where a php-fpm based setup would typically be more appropriate
