创建一个slave 账号
grant replication slave on *.* to 'slave'@'localhost' identified by '123456';

Master 设置
server-id= 1

Slave 设置

server-id = 2
mysql-bin-log
master-retry-time=60

安全模式启动mysql；“mysqld_safe --user=mysql --skip-grant-tables --skip-networking &”

CHANGE MASTER TO
MASTER_HOST='master_host_name',
MASTER_USER='replication_user_name',
MASTER_PASSWORD='replication_password',
MASTER_LOG_FILE='recorded_log_file_name', 	master.status.file
MASTER_LOG_POS=recorded_log_position;		master.status.position


CHANGE MASTER TO
MASTER_HOST='192.168.224.134',
MASTER_USER='slave',
MASTER_PASSWORD='123456',
MASTER_LOG_FILE='mysql-bin.000002',
MASTER_LOG_POS=496;
