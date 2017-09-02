#Version: 0.0.1
FROM opensuse:latest
MAINTAINER Christian Galeffi "chri@gallochri.com"

ENV MYSQL_USER=mysql \
    MYSQL_DATA_DIR=/var/lib/mysql \
    MYSQL_RUN_DIR=/run/mysqld \
    MYSQL_LOG_DIR=/var/log/mysql

RUN zypper --non-interactive dup
RUN zypper in -y mysql-community-server

EXPOSE 3306

