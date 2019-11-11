### Remove root user sudo cmd

```sql
mysql > ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '';
mysql > FLUSH PRIVILEGES;
```
