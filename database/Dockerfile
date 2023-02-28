FROM mysql:5.7

ADD ./build/db.sql /docker-entrypoint-initdb.d

COPY my.cnf /etc/mysql/my.cnf
