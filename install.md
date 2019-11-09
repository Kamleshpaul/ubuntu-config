### Creating new user and give all permission

```sql
CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'password';

GRANT ALL PRIVILEGES ON database_name.* TO 'newuser'@'localhost';
```
