# netstat 查看端口占用

## 1. 命令&参数
```
netstat -tnlp | grep {port}  
```

-t: --tcp    
-n: --numberic  
-l: --listening  
-p: --program   

```
> NAME
>        netstat  -  Print network connections, routing tables, interface statistics, masquerade connections, and multicast mem‐
>        berships
> 
> SYNOPSIS  
>        netstat  [address_family_options]  [--tcp|-t]  [--udp|-u]   [--raw|-w]   [--listening|-l]   [--all|-a]   [--numeric|-n]
>        [--numeric-hosts]  [--numeric-ports] [--numeric-users] [--symbolic|-N] [--extend|-e[--extend|-e]] [--timers|-o] [--pro‐
>        gram|-p] [--verbose|-v] [--continuous|-c]
> 
>        netstat    {--route|-r}    [address_family_options]    [--extend|-e[--extend|-e]]     [--verbose|-v]     [--numeric|-n]
>        [--numeric-hosts] [--numeric-ports] [--numeric-users] [--continuous|-c]
> 
>        netstat   {--interfaces|-i}   [--all|-a]   [--extend|-e[--extend|-e]]   [--verbose|-v]   [--program|-p]  [--numeric|-n]
>        [--numeric-hosts] [--numeric-ports] [--numeric-users] [--continuous|-c]
> 
>        netstat {--groups|-g} [--numeric|-n] [--numeric-hosts] [--numeric-ports] [--numeric-users] [--continuous|-c]
> 
>        netstat {--masquerade|-M} [--extend|-e] [--numeric|-n] [--numeric-hosts] [--numeric-ports] [--numeric-users] [--contin‐
>        uous|-c]
> 
>        netstat {--statistics|-s} [--tcp|-t] [--udp|-u] [--raw|-w]
> 
>        netstat {--version|-V}
> 
>        netstat {--help|-h}
> 
>        address_family_options:
> 
>        [-4]  [-6]  [--protocol={inet,unix,ipx,ax25,netrom,ddp}[,...]]   [--unix|-x]  [--inet|--ip] [--ax25] [--ipx] [--netrom]
>        [--ddp]
```

## 2. 实操
```
(base)  ✘ ⚡ root@localhost  ~/data/redis netstat -tnlp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:25672           0.0.0.0:*               LISTEN      57076/beam.smp
tcp        0      0 127.0.0.1:39498         0.0.0.0:*               LISTEN      1872/containerd
tcp        0      0 127.0.0.1:6379          0.0.0.0:*               LISTEN      10385/redis-server
tcp        0      0 127.0.0.1:3307          0.0.0.0:*               LISTEN      101950/ssh
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      1984/nginx -g daemo
tcp        0      0 0.0.0.0:4369            0.0.0.0:*               LISTEN      57011/epmd
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      2001/sshd
tcp        0      0 172.20.3.150:5432       0.0.0.0:*               LISTEN      2072/postgres
tcp        0      0 127.0.0.1:5432          0.0.0.0:*               LISTEN      2072/postgres
tcp6       0      0 :::5672                 :::*                    LISTEN      57076/beam.smp
tcp6       0      0 :::3306                 :::*                    LISTEN      35516/mysqld
tcp6       0      0 ::1:3307                :::*                    LISTEN      101950/ssh
tcp6       0      0 :::8080                 :::*                    LISTEN      40485/java
tcp6       0      0 :::80                   :::*                    LISTEN      1984/nginx -g daemo
tcp6       0      0 :::4369                 :::*                    LISTEN      57011/epmd
tcp6       0      0 :::22                   :::*                    LISTEN      2001/sshd
tcp6       0      0 127.0.0.1:8005          :::*                    LISTEN      40485/java
```

```
(base)  ⚡ root@localhost  ~  netstat -ntlp | grep 80
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      1984/nginx -g daemo
tcp6       0      0 :::8080                 :::*                    LISTEN      40485/java
tcp6       0      0 :::80                   :::*                    LISTEN      1984/nginx -g daemo
tcp6       0      0 127.0.0.1:8005          :::*                    LISTEN      40485/java
```