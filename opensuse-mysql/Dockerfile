#Version: 0.0.1
FROM opensuse:latest
LABEL maintainer="chri@gallochri.com"
ENV REFRESHED_AT 2017-09-01
ENV MYSQL_ROOT_PASSWORD "mysqlrootpassword"

#Update and install packages
RUN zypper --non-interactive dup && \
    zypper in -y perl && \
    zypper in -y mysql-community-server

RUN mkdir -p /var/lib/mysql
RUN chown -R mysql:mysql /var/lib/mysql
USER mysql:mysql
VOLUME /var/lib/mysql

COPY opensuse-mysql-entrypoint.sh /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]

EXPOSE 3306

CMD ["mysqld","--explicit_defaults_for_timestamp"]
