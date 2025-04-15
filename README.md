### Helpers


### 🧪 Check for OOM Events (Out of Memory Killer Logs)
```bash
sudo grep -i 'oom' /var/log/syslog
```

This shows if any process was killed due to low memory.

---

### 📈 See Top Memory-Consuming Processes
```bash
ps aux --sort=-%mem | head -n 15
```

Lists the top 15 processes sorted by memory usage.

---

### 💾 Show Active Swap
```bash
swapon --show
```

Shows if swap is enabled and how much is in use.

---

### 📊 Show Total Memory and Swap Usage
```bash
free -h
```

Displays memory, used vs. free, and swap usage in human-readable format.

---

### 🧠 Check Memory Pressure (vmstat)
```bash
vmstat 1 5
```

Shows memory, swap, I/O, and CPU stats every 1 second for 5 times.

---


### 🔍 Check System Logs from the Past Minute
If you're watching for a crash:
```bash
sudo journalctl --since "1 minute ago"
```

---

### 🧹 Optional: Clean Cache Memory (careful)
If you're manually tuning:
```bash
sudo sync; echo 3 | sudo tee /proc/sys/vm/drop_caches
```

---

```sql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '';

CREATE USER 'remote'@'%' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON database.* TO 'userName'@'%';
FLUSH PRIVILEGES;

SHOW BINARY LOGS;
PURGE BINARY LOGS BEFORE DATE(NOW() - INTERVAL 3 DAY);

sudo apt autoremove --purge snapd
```
`sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf`

```sh
sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer

sudo usermod -aG docker $(whoami)

sudo update-alternatives --config php 

du -hsx * | sort -rh | head -10

du -h --max-depth=1 /var

sudo ncdu /

sudo netstat -lnp | grep tcp
composer install --optimize-autoloader --no-dev
```

### caddy

```sh
sudo rm -rf var/lib/caddy/.local
```



### docker

```sh
docker system df
docker image prune -a --filter "until=24h"
docker system prune -a
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



```
php -i | grep "\.ini"
```

### change hostname
```sh
sudo nano /etc/hostname

prod
```

```sh
sudo nano /etc/hosts

127.0.1.1 prod

```

## set npm global

```sh
export PATH=~/.npm-global/bin:$PATH
```

# linux space checker
```sh
sudo apt install ncdu
```

# check all open port
```sh
sudo ss -tuln
```
