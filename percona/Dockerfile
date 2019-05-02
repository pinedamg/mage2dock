ARG PERCONA_VERSION=latest
FROM percona/percona-server:${PERCONA_VERSION}

LABEL maintainer="DTUNES <diegotdai@gmai.com>"

RUN chown -R mysql:root /var/lib/mysql/

COPY my.cnf /etc/mysql/conf.d/my.cnf

CMD ["mysqld"]

EXPOSE 3306
