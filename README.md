# m1-wp-docker
This repo contains a setup where you can work with newest Macbook M1s with a containerized setup. Setups such as Lando, Warded among others dont support M1 yet and I got tired of performance issues by using their setup.

## Docker Composer
This is docker-composer based.

## Setup
In order to use docker you need to run:

`docker-compose up --build -d`

You need to provide `WP_DOMAIN` in the .env for docker compose to pick that host up.

Set your /etc/hosts to whatever `WP_DOMAIN` you set, ie : `127.0.0.1 domain.test`

Place any `backup.sql` in the db directory and it should automatically be copied and imported when starting the container.

## Important when it comes to MYSQL
Note that if the mysql dir is not empty, the setup will not create a new database. Ie. Remove any files in `docker-files/mysql` if you wish to recreate the db or do a new import of the database
The import takes a couple of minutes on the first startup. If you close down the container before the import has finished you need to empty and recreate the mysql container in order for it to import the database.
You cant runt the import twice, only once. However if you want to you can always change the symlink to another name, then it will pick it up.
