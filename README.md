# hadoop-hive-docker
Create a Haddop + Hive cluster with Docker

## Credits

This repository was compiled by [Bruno Anglés](https://github.com/tuxsy). The instructions on how to deploy a Hadoop + Hive environment with Docker containers were based on an article by [Hrishi Shirodkar](https://hshirodkar.medium.com/)  published on Medium. You can find the original article [here](https://hshirodkar.medium.com/apache-hive-on-docker-4d7280ac6f8e)). Thank you [Author's Name] for sharing your knowledge and making this project possible!

This set up has been tested on a Macbook Pro with an M2 chip. The Docker Desktop version used was 4.19.0 (106363).


## Quick start
```bash
# start hadoop cluster
export DOCKER_DEFAULT_PLATFORM=linux/amd64
docker-compose up -d


# check hadoop version
docker-compose exec hive-server hadoop version 

# create testdb database
docker-compose exec hive-server hive -f /testdb/employee_table.hql

# load data into testdb.employee table
docker-compose exec hive-server hadoop fs -put /testdb/employee.csv hdfs://namenode:8020/user/hive/warehouse/testdb.db/employee
```

## Test Hive
```bash
# open hive shell
docker-compose exec hive-server hive

# show databases
hive> show databases;

# use testdb
hive> use testdb;

# show tables
hive> show tables;

# select * from employee
hive> select * from employee;
```

## Clean up
```bash
# stop hadoop cluster + remove containers + remove volumes
docker-compose kill && docker-compose down \
    && rm -Rf hdfs && rm -Rf metastore-postgresql
```
