### Access to Postgresql Database
```
mysql -h your_db_endpoint -P 3306 -u your_username -p
```
### Create Database User
```
CREATE USER 'your_username'@'%' IDENTIFIED BY 'your_password';
```
### Grant database user permission
```
GRANT ALL ON *.* TO 'your_username'@'%';
```
```
FLUSH PRIVILEGES;
```

### Backup  and Restore Single Database with plain SQL
- Backup
```
mysqldump -u your_username -p your_database > your_database_backup.sql
```
- Restore
```
mysql -u your_username -p your_database < your_database_backup.sql
```

### Backup  and Restore Single Database Zip Format
- Backup
```
mysqldump -u your_username -p your_database | gzip > your_database_backup.sql.gz
```
- Restore
```
gunzip < your_database_backup.sql.gz | mysql -u your_username -p your_database
```

### Check Current Password Policy on mysql
```
SHOW VARIABLES LIKE 'validate_password%';
```
### Reset MySQL Root Password (Systemd Method)
```
sudo systemctl stop mysqld
```
```
sudo systemctl set-environment MYSQLD_OPTS="--skip-grant-tables --skip-networking"
```
```
sudo systemctl start mysqld
```
### Login without password
```
mysql -u root
```
```
FLUSH PRIVILEGES;
```
```
ALTER USER 'root'@'localhost' IDENTIFIED WITH caching_sha2_password BY 'YouStrongPasswordWithSpecialCharacter';;
```
```
FLUSH PRIVILEGES;
```
### Restore normal startup
```
sudo systemctl stop mysqld
```
```
sudo systemctl unset-environment MYSQLD_OPTS
```
```
sudo systemctl start mysqld
```
### temporary password check
```
sudo grep 'temporary password' /var/log/mysqld.log
```
### Mysql Secure Installation
```
mysql_secure_installation
```

#enable selinux permission (if necessary)
```
semanage port -a -t mysqld_port_t -p tcp 3306
```
### check sestatus related to port 3306
```
 sudo semanage port -l | grep 3306
```

