#Version: 0.0.1
FROM opensuse/leap:latest
LABEL maintainer="chri@gallochri.com"
ENV REFRESHED_AT 2019-07-24
ENV MYSQL_ROOT_PASSWORD "mysqlrootpassword"

#Update and install packages
RUN zypper --non-interactive dup && \
    zypper in -y mariadb

USER mysql:mysql
VOLUME /var/lib/mysql

COPY opensuse-leap-mysql-entrypoint.sh /usr/local/bin/docker-entrypoint.sh
# COPY opensuse-leap-mysql-healthcheck.sh /healthcheck.sh
ENTRYPOINT ["docker-entrypoint.sh"]
HEALTHCHECK CMD /healthcheck.sh

EXPOSE 3306

CMD ["mysqld","--explicit_defaults_for_timestamp"]
