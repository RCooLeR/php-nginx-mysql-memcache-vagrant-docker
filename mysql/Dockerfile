FROM mysql:5.5

RUN sed -i -e"s/^bind-address\s*=\s*127.0.0.1/bind-address = 0.0.0.0/" /etc/mysql/my.cnf
COPY ./conf/my.cnf /etc/mysql/conf.d/my_conf.cnf
COPY ./dump/last.sql /tmp/last.sql
COPY ./scripts/ /docker-entrypoint-initdb.d/
