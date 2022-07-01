# drupal8dev

Drupal 8 dev playground using docker.

Using official Drupal 8 docker images, and using volumes for modules, themes and profiles which gets mapped to same folders inside the drupal container.

On OSX docker is slow because of slow mounts, so we are using docker-sync (http://docker-sync.io/)

# Usage

0. If using your own database, place sql file in ./backup folder.
1. Copy .env-dist to .env and change ports for your environment if needed.
2. In root where we have docker-sync.yml file, start docker sync i.e. docker-sync start
3. Start docker compose e.g. docker-compose up -d
4. admin user is admin and password is admin.
5. Destroy env (take a backup using instructions below, if you want) e.g. docker-compose down.

# Take backup of your development database

Use ./backup_db.sh this will create a backup called all-databases.gz inside ./backup folder. As official mysql container starts and any "sql" file in "docker-entrypoint-initdb.d" folder, which is mapped to ./backup folder is restored when mysql starts.

Just remember to gunzip the .gz into a sql file before you start the environment.

i.e. gzip -d ./backup/all-databases.gz all-databases.sql

