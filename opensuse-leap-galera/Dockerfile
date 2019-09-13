#Version: 0.0.1
FROM opensuse/leap:15.1
LABEL maintainer="chri@gallochri.com"

ENV REFRESHED_AT 2019-09-13
ENV MYSQL_ROOT_PASSWORD "mysqlrootpassword"

RUN zypper ar -Gf http://download.opensuse.org/repositories/server:/database/openSUSE_Leap_15.1/ server:database
RUN zypper --non-interactive dup -y
RUN zypper install -y mariadb mariadb-galera galera-3
RUN mkdir -p /var/lib/mysql
RUN chown -R mysql:mysql /var/lib/mysql
USER mysql:mysql
VOLUME /var/lib/mysql

COPY 50-galera.cnf /etc/my.cnf.d/50-galera.cnf
COPY opensuse-leap-mysql-entrypoint.sh /usr/local/bin/docker-entrypoint.sh
ENTRYPOINT ["docker-entrypoint.sh"]

EXPOSE 8306

CMD ["mysqld","--explicit_defaults_for_timestamp"]