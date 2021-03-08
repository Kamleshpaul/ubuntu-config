### Remove root user sudo cmd

```sql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '';

CREATE USER 'remote'@'%' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON database.* TO 'userName'@'%';
FLUSH PRIVILEGES;
```

```sh
sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer

sudo usermod -aG docker $(whoami)

sudo update-alternatives --config php 

du -hsx * | sort -rh | head -10

sudo netstat -lnp | grep tcp

```


https://www.websitevidya.com/fix-504-gateway-timeout-nginx-error/ 

nginx timeout

Step 1 :
```sh
sudo vim /etc/php/7.4/fpm/php.ini
```
Now, search for the `max_execution_time`

make it `max_execution_time = 300`

Step 2 :

```sh
sudo vim /etc/php/7.4/pool.d/www.conf
```
Now, search for the `request_terminate_timeout`

make it `request_terminate_timeout = 300`

Step 3 :

```sh
sudo vim /etc/nginx/sites-available/example.com

location ~ \.php$ {
include /etc/nginx/fastcgi_params;
fastcgi_pass unix:/var/run/php5-fpm.sock;
fastcgi_read_timeout 300;
}
```
add `fastcgi_read_timeout 300;` 

Step 4 :

```sh
sudo vim /etc/nginx/nginx.conf
```
add lines

```sh
fastcgi_buffers 8 16k;
fastcgi_buffer_size 32k;
fastcgi_connect_timeout 300;
fastcgi_send_timeout 300;
fastcgi_read_timeout 300;
```

then restart server
