# Ceph Tool Scripts

ceph script toolbox to help develop, operate and test ceph easily.

## deployer

Ceph deploying toolbox.

- deploy\_on\_single\_node.sh: help you deploy ceph on a single host from yum source.
- install\_build\_ceph.sh: help you deploy ceph on a single host from source code.
- add\_blue\_osd.sh: add bluestore osd.
- add\_mgr.sh: add mgr into cluster.
- add\_osd.sh: add filestore osd.

... ...

## operater

... ...

## tester

Test toolbox for ceph.

### mclock\_tester

1. How to use

You can use it test ceph pool-unit QoS based dmclock. The implementation of it is [here](https://github.com/bspark8/ceph/tree/wip-pool-unit-dmclock).

- mclock\_test.cfg: configuration file of mclock\_tester.
- dmclock\_test\_script2.sh: dmclock test script
- xx\_qos\_configs.csv: add test case into this file, eg:

16K\_qos\_configs.csv:

```
id,r,w,l
0,1 1 1 1 1,1 1 1 1 1,0 0 0 0 0
1,2000 2000 2000 2000 0,1 1 1 1 1,0 0 0 0 0
2,0 0 0 0 3500,1 1 1 1 1,0 0 0 0 0
3,0 1000 3000 1500 0,1 1 1 1 1,0 0 0 0 0
4,500 1000 1500 2000 2500,1 1 1 1 1,0 0 0 0 0
```

Just run `dmclock\_test_script2.sh` after modifying mclock\_test.cfg. And suggest opening a tmux window and run this script in it.

```
./dmclock_test_script2.sh
```

2. Get results and graphes

You can get result in result directory which is set in mclock\_test.cfg, eg: 16K\_result\_iops\_190814183036.csv.

You can also get fio log file and draw it using gnuplot. Run following command in path where script runs:

```
fio2gnuplot -i -g
```

3. Others

You can also use these script alone:

- create\_pools.sh: to create pools in batch.
- create\_rbds.sh: to create rbds on corresponding pool.
- remove\_pools.sh: to remove pools in batch.
- remove\_rbds.sh: to remove rbds in batch.
- fio\_rw\_dmclock.sh: use fio to test dmclock.
- send\_dmclock\_test\_result.sh: to send test result to your email.
- clean\_rados.sh: to kill all rados processes.

## contributing

### Log level

There are three log levels: INFO, WARN and ERROR. 

The return code is very simple:

- INFO: program return 0
- WARN: program return 1
- ERROR: program return -1

So you should add detailed description in log.

### License

![gpl-license](https://www.gnu.org/graphics/gplv3-127x51.png)

Software License Agreement(GPL License) 

Ceph scrit toolbox. 

Copyright (c) 2019, Liu Chaoyang

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program. If not, see http://www.gnu.org/licenses/.
