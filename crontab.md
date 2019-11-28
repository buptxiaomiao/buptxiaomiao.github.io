# CRONTAB

- 配置文件 `/etc/crontab`

- 服务 `systemctl status/restart/stop crond`

- crontab日志 `/var/log/cron `

- `crontab -e/-l` 实际的文件：`/var/spool/cron/$USER`
- **在/etc/crontab 文件中添加的crontab任务，不会显示到crontab -l中**

- crontab执行最小时间粒度：分钟  


## 架构：
`/var/spool/cron/$USER` 文件变更后，`cron-server`解析提交给`crond服务`  

## 配置
`* * * * *`  `分 时 日 月 周`  
i-j表示  i到j  
,分隔来枚举  
*/10 每多久

线上测试地址：http://cron.schlitt.info/index.php
