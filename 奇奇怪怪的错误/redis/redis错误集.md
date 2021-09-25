# redis错误集

## 1、不能持久化到硬盘

**==问题==**：MISCONF Redis is configured to save RDB snapshots, but is currently not able to persist on disk. Commands that may modify the data set are disabled. Please check Redis logs for details about the error.
 Redis被配置为保存数据库快照，但它目前不能持久化到硬盘。用来修改集合数据的命令不能用。请查看Redis日志的详细错误信息。



**==原因==**：强制关闭Redis快照导致不能持久化。



**==解决方案==**：将stop-writes-on-bgsave-error设置为no

```shell
> 10.10.103.154 connected!
> config set stop-writes-on-bgsave-error no
OK
```



