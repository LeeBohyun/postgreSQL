# How to Run TPC-C Benchmark on PostgreSQL
- You have to use the benchmarking tool provided by [HammerDB](https://github.com/TPC-Council/HammerDB).
- [Reference](https://www.hammerdb.com/docs/)
- HammerDB requires glibc-2.29 or higher (so you better use ubuntu-20.04)


## How to setup Postgres 
1. Add the LD_LIBRARY at ```.bash_profile``` and ```/etc/ld.so.conf```.
```bash
$ vim /etc/ld.so.conf
$ /home/postgres/postgresql-9.4.5/build/lib <- add
$ ldconfig

$ vim .bash_profile
$ export PATH=/home/postgres/postgresql-9.4.5/build/lib 
$ source .bash_profile
```

2. Run postgreSQL server
```bash
$ pg_ctl -D /home/postgres/test_data -l /home/postgres/test_log/pg_log/logfile start
```

## How to install HammerDB
0. Prerequisites
```bash
sudo apt-get install tcl-thread
sudo apt-get install tkblt
sudo apt install cmake build-essential tcl-dev tk-dev python3-tk
python3 -m pip install scikit-build
```

1. Download and unzip the sourcecode to directory ```/home/postgres/```.
```bash
$ su - postgres
$ wget https://github.com/TPC-Council/HammerDB/releases/download/v4.6/HammerDB-4.6-Linux.tar.gz
$ tar -zxvf HammerDB-4.6.tar.gz
```

2. Run HammerDB and start load & run data. Refer to this link for guide for quick start. [Quick Start](https://www.hammerdb.com/docs/ch02.html)
```bash
./hammerdb
```

