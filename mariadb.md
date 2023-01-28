在 MariaDB 中新建用户的语法如下：

Copy code
CREATE USER 'username'@'host' IDENTIFIED BY 'password';
其中：

username 是新建用户的用户名。
host 是该用户可以连接到数据库服务器的主机名或 IP 地址。可以使用通配符 % 代表所有主机。
password 是该用户的密码。
如果要赋予新建用户权限，需要使用 GRANT 语句。

例如:

Copy code
GRANT ALL PRIVILEGES ON *.* TO 'username'@'host';
这样就可以赋予新建用户所有权限。

最后,记得要刷新权限使其生效

Copy code
FLUSH PRIVILEGES;

在 Ubuntu 上，MariaDB 的配置文件通常位于 /etc/mysql/mariadb.conf.d 目录中。

在这个目录中，可能有多个配置文件，比如 my.cnf 和 50-server.cnf。这些文件都会被加载并使用。