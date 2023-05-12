# hadoop-hive-docker
Create a Haddop + Hive cluster with Docker

Thankks to [Hrishi Shirodkar](https://hshirodkar.medium.com/) for this article in Medium: [Apache Hive on Docker
](https://hshirodkar.medium.com/apache-hive-on-docker-4d7280ac6f8e).

# Quick start

```bash
# start hadoop cluster
export DOCKER_DEFAULT_PLATFORM=linux/amd64
docker-compose up -d


# check hadoop version
docker-compose exec hive-server hadoop version 

# create testdb database
docker-compose exec hive-server hive -f /testdb/employee_table.hql


# Clean up
docker-compose kill && docker-compose down \
    && rm -Rf hdfs && rm -Rf metastore-postgresql
```
