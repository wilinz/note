# Openwrt 记录

## 1. 替换ash为bash

1. ```shell
   opkg install bash
   ```

   

2. ```shell
   nano /etc/passwd
   ```

   

3. 将 /bin/ash 替换为 /bin/bash

## 2. 安装全功能 ps 命令

默认的ps来自busybox。该功能不完整，不支持 aux、ef 选项

```shell
opkg install procps-ng-ps
```



## 3. 程序自启动脚本例子，/etc/init.d/xxx

~~~shell
#!/bin/sh /etc/rc.common

START=20
STOP=90

start() {
       SERVICE="ddns1"
        if [ -f "/var/run/${SERVICE}.pid" ]; then
            echo "${SERVICE} is running with pid $(cat "/var/run/${SERVICE}.pid")"
        else
            echo "Starting ddns1 at $(date)" >> /tmp/ddns1.log
            /root/ddns1 >> /tmp/ddns1.log 2>&1 &
            pid=$(ps -ef | grep ${SERVICE} | grep -v grep | awk '{print $2}')
            echo $pid > /var/run/${SERVICE}.pid
        fi
}

stop() {
       echo "Stopping ddns1 at $(date)" >> /tmp/ddns1.log
       SERVICE="ddns1"
       kill $(cat /var/run/${SERVICE}.pid)
       rm /var/run/${SERVICE}.pid
}

restart() {
       stop
       sleep 1
       start
}

~~~

