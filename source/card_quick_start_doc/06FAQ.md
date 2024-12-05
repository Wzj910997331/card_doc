
## AXCL FAQ

### 1. 抓取设备侧日志

**axcl_smi** 工具支持将设备侧的日志（内核和SDK的syslog，运行时库日志）抓取到Host本地，使用方法如下：

```bash
  ./axcl_smi COMMAND {OPTIONS}

  OPTIONS:

      commands
        log                               dump log from slave
      arguments for <log> command
        -d[device], --device=[device]     device, default 0
        -t[type], --type=[type]           type: -1: all, bit mask: 0x01: daemon;
                                          0x02: worker; 0x10: syslog; 0x20:
                                          kernel
        -o[output], --output=[output]     output
```

示例如下：

```bash
[test@centos bin]$ ./axcl_smi log -t -1
command is log
log type is -1
file sink initialization failed: Failed opening file /tmp/axcl/axcl_logs.txt for writing: Permission denied
[11-20 18:13:51:899][E][axcl_smi][main][ 117]: device id: 1
[2024-11-20 18:13:52.356][290043][C][control][dump][72]: log dump finished: ./log_20241120181346.tar.gz
[test@centos bin]$
```

