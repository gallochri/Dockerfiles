#Version: 0.0.1
FROM opensuse/leap:15.1
LABEL maintainer="chri@gallochri.com"
LABEL descriptor="MariaDB daabase with galera"

ENV REFRESHED_AT 2019-09-13
ENV MYSQL_ROOT_PASSWORD "mysqlrootpassword"

COPY files/rpm-import-repo-key /
RUN chmod +x /rpm-import-repo-key && \
    sync && /rpm-import-repo-key 116EB86331583E47E63CDF4D562111AC05905EA8 && \
    zypper ar -f obs://server:database/openSUSE_Leap_15.1 database && \
    zypper clean -a && \
    rm /rpm-import-repo-key
RUN zypper --non-interactive dup
RUN zypper install -y mariadb mariadb-galera galera-3
RUN mkdir -p /var/lib/mysql &&\
    chown -R mysql:mysql /var/lib/mysql
RUN mysql_install_db

USER mysql:mysql
VOLUME /var/lib/mysql

COPY files/50-galera.cnf /etc/my.cnf.d/50-galera.cnf
COPY opensuse-leap-mysql-entrypoint.sh /usr/local/bin/docker-entrypoint.sh
ENTRYPOINT ["docker-entrypoint.sh"]

EXPOSE 3306

CMD ["mysqld"]
#CMD ["mysqld","--explicit_defaults_for_timestamp"]