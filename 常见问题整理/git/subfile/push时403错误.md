执行完 git push后：

```git
Push failed: Failed with error: unable to access 'https://github.com/*******/': 
OpenSSL SSL_connect: SSL_ERROR_SYSCALL in connection to github.com:443
```

解决方案：

- **清除dsn缓存**

cmd 命令行执行 ipconfig/flushdns

cmd 命令行执行 ipconfig/flushdns

```
ipconfig/flushdns
```

