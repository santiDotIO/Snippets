# shell-scripts
compilation of shell scripts and aliases 

## newUser.sh

``` sh
if [ -n $1 ]; then 
	adduser --gecos "" $1;
	echo >> /etc/sudoers "$1    ALL=(ALL:ALL) ALL";
	sudo groupadd www-data;
	sudo adduser $1 www-data;
	sudo usermod -g www-data $1;
	sudo chown -R www-data:www-data /var/www/;
	sudo chmod -R g+w /var/www/;
	service ssh restart;
else
	echo "no username specified" 
	exit 1
fi
```