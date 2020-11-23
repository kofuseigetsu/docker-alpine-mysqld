# MySQL Server Docker image on Alpine Linux

This is the MySQL Server (mysqld) image on Alpine Linux.

## How to use this image

```
docker run -d --rm --name alpine-mysqld -p 3306:3306 -e MYSQL_ROOT_PASSWORD=passwordOfRoot -e MYSQL_DATABASE=databasenmae -e MYSQL_USER=username -e MYSQL_PASSWORD=userpassword seigetsu/alpine-mysqld:3.12
```

## Data Volume

`/var/lib/mysql` : 

Database data is stored here.
The data remains until the container is deleted.
If you need persistence, mount this directory on your host system.

## Tags

- `:<baseimage-tag>` : latest version of this image based on the image of `alpine:<baseimage-tag>`.
- `:<baseimage-tag>-<version>` : Specific version of this image based on the image of `alpine:<baseimage-tag>`.

## Environment Variables

- `MYSQL_ROOT_PASSWORD` : Password for root user. Don't specified if use `MYSQL_RANDOM_ROOT_PASSWORD`.
- `MYSQL_RANDOM_ROOT_PASSWORD` : Set to `yes` (no-empty) to create random password for root user. Don't specified if use `MYSQL_ROOT_PASSWORD`.
- `MYSQL_DATABASE` : Database name to be created.
- `MYSQL_USER` : User for the database.
- `MYSQL_PASSWORD` : User password.

## Relationship between Source code and Docker image tag

- `<baseimage-tag>` : see directory.
- `<version>` : see branch.

Example:

`seigetsu/alpine-mysqld:3.12-v1.0` :

- branch `v1.0`
- directory `3.12`

## Automated Build configurations

- SOURCE REPOSITORY : `kofuseigetsu/docker-alpine-mysqld`
- AUTOTEST : `Off`
- REPOSITORY LINKS : `Off`
- BUILD RULES :  
  | Source Type | Source | Docker Tag | Dockerfile location | Build Context | Autobuild | Build Caching |
  | -------| -------------- | --------------- | ---------- | ----------- | --- | --- |
  | Branch | main           | 3.12            | Dockerfile | /3.12       | Yes | No  |
  | Branch | /^(v[0-9.]+)$/ | 3.12-{\1}       | Dockerfile | /3.12       | Yes | No  |
