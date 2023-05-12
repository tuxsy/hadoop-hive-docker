FROM postgres:15.3  
# old version was 9.5.3

# MAINTAINER "Ivan Ermilov <ivan.s.ermilov@gmail.com>"
LABEL author="Ivan Ermilov <ivan.s.ermilov@gmail.com>"
LABEL updated_by="Bruno Anglés Robles <bangles@gmail.com>"

COPY hive-schema-2.3.0.postgres.sql /hive/hive-schema-2.3.0.postgres.sql
COPY hive-txn-schema-2.3.0.postgres.sql /hive/hive-txn-schema-2.3.0.postgres.sql
COPY upgrade-2.3.0-to-3.0.0.postgres.sql /hive/upgrade-2.3.0-to-3.0.0.postgres.sql
COPY upgrade-3.0.0-to-3.1.0.postgres.sql /hive/upgrade-3.0.0-to-3.1.0.postgres.sql

COPY init-hive-db.sh /docker-entrypoint-initdb.d/init-user-db.sh
RUN chmod +x /docker-entrypoint-initdb.d/init-user-db.sh