# How to Run TPC-C Benchmark on PostgreSQL
- You have to use the benchmarking tool provided by [HammerDB](https://github.com/TPC-Council/HammerDB).
- [Reference](https://www.hammerdb.com/docs/)



## How to install HammerDB
0. Prerequisites
```bash
sudo apt-get install tcl-thread
sudo apt-get install tkblt
sudo apt install cmake build-essential tcl-dev tk-dev python3-tk
python3 -m pip install scikit-build
```

1. Download and unzip the sourcecode.
```bash
$ wget https://github.com/TPC-Council/HammerDB/releases/download/v4.6/HammerDB-4.6-Linux.tar.gz
$ tar -zxvf HammerDB-4.6.tar.gz
$ export DISPLAY=:0


```
