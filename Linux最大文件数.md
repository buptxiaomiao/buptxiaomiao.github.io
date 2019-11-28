# Linux查看最大文件数

## 1. 进程最大文件数
```
(base)  ⚡ root@localhost  ~/bin ulimit -n
1024


(base)  ⚡ root@localhost  ~/bin ulimit -a
-t: cpu time (seconds)              unlimited
-f: file size (blocks)              unlimited
-d: data seg size (kbytes)          unlimited
-s: stack size (kbytes)             8192
-c: core file size (blocks)         0
-m: resident set size (kbytes)      unlimited
-u: processes                       31707
-n: file descriptors                1024
-l: locked-in-memory size (kbytes)  64
-v: address space (kbytes)          unlimited
-x: file locks                      unlimited
-i: pending signals                 31707
-q: bytes in POSIX msg queues       819200
-e: max nice                        0
-r: max rt priority                 0
-N 15:                              unlimited
```

##### 临时修改
```
(base) root@localhost:~# sh
# ulimit -n
1024

# ulimit -n 1111
# ulimit -n
1111
# exit

# 在当前shell 修改文件数， 退出shell即失效
(base) root@localhost:~# ulimit -n
1024
```
##### 永久修改
```
# todo: 好像有问题
(base)  ⚡ root@localhost  ~ echo "* soft nofile 65535" >> /etc/security/limits.conf
(base)  ⚡ root@localhost  ~  echo "* hard nofile 65535" >> /etc/security/limits.conf
```


----

## 2. 系统最大文件数--所有进程可以打开的文件数量
```
(base)  ⚡ root@localhost  ~/bin cat /proc/sys/fs/file-max
809321
```

##### 临时修改
```
(base)  ⚡ root@localhost  ~ cat /proc/sys/fs/file-max
809321
(base)  ⚡ root@localhost  ~ echo 11111111 >> /proc/sys/fs/file-max
(base)  ⚡ root@localhost  ~  cat /proc/sys/fs/file-max
11111111
```

##### 永久修改
```
(base)  ⚡ root@localhost  ~  echo "fs.file-max=22222222" >> /etc/sysctl.conf
(base)  ⚡ root@localhost  ~  cat /etc/sysctl.conf | grep fs
fs.file-max=22222222
```

