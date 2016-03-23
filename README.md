Development environment boilerplate(Wordpress with total cache tested): php7; nginx; mysql; memcached(php-memcache); vagrant; docker

###Using:

1. Install dependencies: run `vagrant plugin install vagrant-docker-compose`
1. Add project files to app directory
1. Edit configurations if needed (mysql/conf; nginx/conf etc.)
1. Run `vagrant up`
1. Add record `192.168.99.100 app.host` to your hosts file  
1. [http://app.host](http://app.host)
