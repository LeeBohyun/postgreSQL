# How to Run Sysbench on Postgres
- [References](https://severalnines.com/blog/how-benchmark-postgresql-performance-using-sysbench/)

## Installing Sysbench and PostgreSQL
- Install sysbench according to this guide: [Installation Guide](https://github.com/LeeBohyun/sysbench/blob/master/sysbench.md).
- wget http://repo.percona.com/apt/pool/main/s/sysbench/sysbench_1.0.20.orig.tar.gz
- Install postgres according to this guide: [Installation Guide](https://github.com/LeeBohyun/postgreSQL/blob/main/postgres-installation-guide.md)

- Ass pgsql libraries to sysbench directory.
```bash

CFLAGS="-L/home/postgres/postgresql-9.4.5/build/lib -I/home/postgres/postgresql-9.4.5/build/include -lpq" 
./configure --prefix=/home/postgres/sysbench-1.0.20  --with-pgsql \
--with-pgsql-includes=/home/postgres/postgresql-9.4.5/build/include --with-pgsql-libs=//home/postgres/postgresql-9.4.5/build/lib
make
make install
```

## Run the Test
1. Create DB 
```bash
$ su - postgres
$ psql
> CREATE USER sbtest WITH PASSWORD 'password';
> CREATE DATABASE sbtest;
> GRANT ALL PRIVILEGES ON DATABASE sbtest TO sbtest;
>\q
```
2. Connect to the testing DB
```bash
$ psql -U sbtest -h localhost -p 5432 -W
```
4. Load the data 
```bash
$ sysbench \
--db-driver=pgsql \
--oltp-table-size=2000000 \
--oltp-tables-count=24 \
--threads=32 \
--pgsql-host=localhost \
--pgsql-port=5432 \
--pgsql-user=sbtest \
--pgsql-password=evia6587 \
--pgsql-db=sbtest \
/home/postgres/sysbench-1.0.20/tests/include/oltp_legacy/parallel_prepare.lua \
run
```
