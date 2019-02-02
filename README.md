#  Docker-Webserver
#### Docker-Webserver is a simple docker-compose deployment of Apache2, PHP 7.0 and MySQL 5.5 (which is the latest version for ARM-based devices).
#### The php extensions are preconfigured for a basic NextCloud install.
#### The apache2-php container is based on Debian.

# Getting started with NextCloud on Docker-Webserver
- Install `docker` and `docker-compose`
- Download the NextCloud zip and copy the nextcloud directory of the unzipped file to the `webroot` directory
- run `fix_permissions.sh`
- modify `DOCKER_WEBSERVER_PATH` inside `docker-webserver.sh` to match your installation directory 
- modify `COMPOSE_FILE` inside `docker-webserver.sh` to
    - amd64.yaml (AMD64)
    - armhf.yaml (ARM)
- change `AUTH_PASSWORD` inside your `.yaml` file to a strong password if you are using authentication
    - (optional) change `AUTH_USERNAME` too
- open your webbrowser and open the IP address of the computer running the Docker-Webserver installation at port 8081
- use the 
    - `MYSQL_USER` (username)
    - `MYSQL_PASSWORD` (password)
    - `MYSQL_DATABASE` (database name) and
    - database service name (`database` per default) values from your `.yaml` file to fill out the database connection form

## Server Control
- start the server by running `docker-webserver.sh` or `docker-webserver.sh start`
- to stop the server just run `docker-webserver.sh stop`
- to stop the server and delete the docker containers, run `docker-webserver.sh delete`.
- to rebuild the images and start the server, run `docker-webserver.sh build`.

## Server Autostart
If you want to automatically start docker-webserver when starting your computer, you can e.g. create a cron job that runs docker-webserver.sh.

## Backups
Your database will be stored in the `mysql-data` directory and your website data will be stored in `webroot`.  
You can easily make a backup of your server data by copying these directories to your backup target.

## Legacy Software
For compatibility reasons to ARMHF, this project uses MySQL 5.5.
This may change as newer versions become available as docker images for ARMHF.

## Copyright & License
Copyright (c) 2018 ahahn94.

docker-webserver is free software; you can redistribute it and/or
modify it under the terms of the GNU General Public License
as published by the Free Software Foundation; either version 2
of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program; if not, write to the Free Software
Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.