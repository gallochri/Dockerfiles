#Version: 0.0.1
FROM opensuse/leap:15.1
LABEL maintainer="chri@gallochri.com"
LABEL descriptor="MariaDB daabase"

ENV REFRESHED_AT 2019-09-16
ENV MYSQL_ROOT_PASSWORD "mysqlrootpassword"

#Update and install packages
RUN zypper --non-interactive dup && \
    zypper in -y mariadb
RUN mkdir -p /var/lib/mysql &&\
    chown -R mysql:mysql /var/lib/mysql
RUN mysql_install_db

USER mysql:mysql
VOLUME /var/lib/mysql

COPY opensuse-leap-mariadb-entrypoint.sh /usr/local/bin/docker-entrypoint.sh
COPY opensuse-leap-mariadb-healthcheck.sh /healthcheck.sh
ENTRYPOINT ["docker-entrypoint.sh"]
HEALTHCHECK CMD /healthcheck.sh

EXPOSE 3306

CMD ["mysqld","--explicit_defaults_for_timestamp"]
