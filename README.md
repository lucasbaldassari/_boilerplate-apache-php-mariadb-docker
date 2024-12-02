# \_boilerplate-apache-php-mariadb-docker

Boilerplate to start a development project using Apache, PHP, MariaDB and Docker.

**Versions:**

-   Apache 2.4.62
-   PHP 8.4.1
-   MariaDB 11.4.3

**PHP extensions** (can be changed in `.docker/server/Dockerfile`):

-   gd
-   imagick
-   intl
-   pdo_mysql
-   sodium
-   xdebug
-   zip

File `php.ini` is in the `.docker/server/php-config` folder. Apache document root is `/var/www/html/public`. It can be changed in the `.docker/server/Dockerfile` file.

### Setup

1. Clone the project:

```sh
$ git clone https://github.com/lucasbaldassari/_boilerplate-apache-php-mariadb-docker.git
```

2. Rename the folder for your project:

```sh
$ mv _boilerplate-apache-php-mariadb-docker YOUR_PROJECT_FOLDER_NAME_HERE
```

3. Enter the folder:

```sh
$ cd YOUR_PROJECT_FOLDER_NAME_HERE
```

4. Give execute permission to the following file:

```sh
$ chmod +x setup.sh
```

5. Set the variables that are at the top of the `setup.sh` according to your needs.

6. Run the `setup.sh` file:

```sh
$ ./setup.sh
```

7. Done! The boilerplate is configured and Docker is ready to run!

### Initialize all containers (only first run)

1. Set the appropriate `date.timezone` in `.docker/server/php-config/php.ini`.
2. Run the following command:

```sh
$ ./.docker/init.sh
```

### Get into server's container shell

```sh
$ ./.docker/bash.sh
```

### Stop all containers (once initialized)

```sh
$ ./.docker/stop.sh
```

### Resume all containers (once initialized)

```sh
$ ./.docker/start.sh
```

### Kill all containers and remove the database folder

```sh
$ ./.docker/destroy.sh
```

### Inspect network IP

```sh
$ ./.docker/network.sh
```

### Debug settings for Visual Studio Code

Use the following settings in the `.vscode/launch.json`:

```json
{
    "name": "PHP Debug With Docker",
    "type": "php",
    "request": "launch",
    "port": 9003,
    "pathMappings": {
        "/var/www/html": "${workspaceFolder}"
    }
}
```
