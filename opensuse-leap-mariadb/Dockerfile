#Version: 0.0.1
FROM gallochri/leap:15.1
LABEL maintainer="chri@gallochri.com"
LABEL descriptor="MariaDB daabase"

ENV REFRESHED_AT 2019-09-17

RUN zypper install -y mariadb
ADD bind-any.cnf /etc/my.cnf.d/

# Setup mariadb
RUN /usr/lib/mysql/mysql-systemd-helper install; \
    /usr/lib/mysql/mysql-systemd-helper start & \
    /usr/lib/mysql/mysql-systemd-helper wait; \
    /usr/bin/mysql -u root -e "SELECT @@version; CREATE USER 'root'@'%' IDENTIFIED BY 'opensuse'; GRANT ALL ON *.* TO 'root'@'%' WITH GRANT OPTION;"; \
    mysqladmin shutdown

EXPOSE 3306

USER mysql:mysql
CMD ["mysqld"]