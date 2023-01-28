要在 Redis 中设置密码，您需要编辑 Redis 的配置文件并修改 requirepass 选项。

nano /etc/redis/redis.conf

将 foobared 替换为您想要使用的密码。

重启：/etc/init.d/redis-server restart