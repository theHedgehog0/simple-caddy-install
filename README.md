# A Simple Caddy Installation

## Follow these steps to get caddy working with php-fpm on debian!
## Read through this once and ask Aaron if you have any questions!

1. Login to your server
2. Run these commands, one at a time:
```sh
sudo apt install -y debian-keyring debian-archive-keyring apt-transport-https
curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/gpg.key' | sudo tee /etc/apt/trusted.gpg.d/caddy-stable.asc
curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/debian.deb.txt' | sudo tee /etc/apt/sources.list.d/caddy-stable.list
sudo apt update
sudo apt install caddy php-fpm
sudo nano /etc/caddy/Caddyfile
```
3. Change line 21 from 
```
	# php_fastcgi localhost:9000
```
to 
```
  php_fastcgi unix//run/php/php-fpm.sock
```
4. Change line 13 from
```
	root * /usr/share/caddy
```
to 
```
  root * /home/<your username>/www
```
5. Exit `nano`.
6. Run `cd ~`.
7. Run `mkdir www`
8. Run `nano www/index.php`
9. Add the following to the file:
```php
<? php
phpinfo();
?>
```
10. Open your web browser and navigate to your Pi's URL.
11. If you see a long page of details, congratulations! You have installed Caddy and PHP-FPM successfully, and everyting is working!
# Let Aaron know if you have any questions!!
