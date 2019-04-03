Install MariaDB 10.3
```
vi /etc/yum.repos.d/MariaDB.repo
-----
# MariaDB 10.3 CentOS repository list - created 2019-04-03 02:44 UTC
# http://downloads.mariadb.org/mariadb/repositories/
[mariadb]
name = MariaDB
baseurl = http://yum.mariadb.org/10.3/centos7-amd64
gpgkey=https://yum.mariadb.org/RPM-GPG-KEY-MariaDB
gpgcheck=1
-----
sudo yum install -y MariaDB-server MariaDB-client
```

Create default password
```
mysql_secure_installation
```

Create config file
```
vi /etc/my.cnf
-----
[mysqld]
#server-id = 2
#replicate-do-db = xxx
#replicate-ignore-db = mysql
#slave-skip-errors = 1062,1032,1205,1366,1061

#sql-mode=""
#innodb_file_per_table
innodb_buffer_pool_size = 4G
innodb_flush_method = O_DIRECT
#innodb_read_only = 1

#slow-query-log = 1
#slow-query-log-file = /var/log/mysql/mysql-slow.log
#long_query_time = 5

# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
# As of 5.1 you can enable the log at runtime!
#general_log_file = /var/log/mysql/mysql.log
#general_log = 1
log_error = /var/log/mysql/mysql_error.log
```
