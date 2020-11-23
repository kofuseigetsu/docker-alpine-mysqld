FROM alpine:3.12

RUN addgroup -S mysql && adduser -S mysql -G mysql

# install

# Version 10.2 and above of mysql may not work properly when datadir is mounted.
RUN apk update && echo 'http://dl-cdn.alpinelinux.org/alpine/v3.7/main' >> /etc/apk/repositories
RUN apk add 'mysql<10.2' 'mariadb<10.2' 'mariadb-common<10.2' 'mysql-client<10.2' pwgen --no-cache || true

# entry point
COPY alpine-mysqld-entrypoint.sh /usr/local/bin
RUN chmod -R +x /usr/local/bin

VOLUME ["/var/lib/mysql"]

EXPOSE 3306

ENTRYPOINT ["alpine-mysqld-entrypoint.sh"]
