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