# How to Install & Run postgreSQL with Sourcecode
This installation guide is limited to linux environment.

## Installation Procedures
0. Create a user and login to postgres account. If you are using separate devices for data and log storage, you need to mount them to ```/home/postgres/``` as well.
```bash
$ adduser postgres
$ su - postgres
```

1. Download the source code from the postgreSQL [website](https://www.postgresql.org/ftp/source/).
```bash
$ wget https://ftp.postgresql.org/pub/source/v9.4.5/postgresql-9.4.5.tar.gz
```

2. Untar the sourcecode.
```bash
$ tar -xvzf postgresql-9.4.5.tar.gz 
```

3. Create a new directory to build and configure the source tree. Then build and install the sourcecode.
```bash
$ cd postgresql-9.4.5
$ mkdir build
$ ./configure --prefix=/home/postgres/postgresql-9.4.5/build
$ make -j install
```

4. Then add the shared library path to ```~/.bashrc```. Then apply the change.
```bash
vim ~/.bashrc
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/postgres/postgresql-9.4.5/build/lib
export PATH=/home/postgres/postgresql-9.4.5/build/bin:$PATH

source ~/.bashrc
```

## How to Start PostgreSQL Server
1. Initialize the database storage with ```initdb``` command of postgres. You can dedicate a data directory using -D option.
```bash
$ initdb -D /home/postgres/test_data
$ initdb --encoding=UTF-8 --no-locale --username=root --pgdata=/home/postgres/test_data
```

2. Start the database server with logfile. You can modify the configurations with ```postgresql.conf``` file inside a data directory.
```bash
$ pg_ctl -D /home/postgres/test_data -l logfile start
```

3. End the database server.
```bash
$ pg_ctl -D /home/postgres/test_data -m smart stop
```

## References
- https://github.com/meeeejin/til/blob/master/postgresql/installation-from-source-code.md
- https://www.postgresql.org/docs/11/installation.html
- https://github.com/hundredbag/til/blob/master/Databases/PostgreSQL/psql_install_init.md
