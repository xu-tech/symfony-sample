FROM phpdockerio/php74-fpm:latest
WORKDIR "/application"

# Fix debconf warnings upon build
ARG DEBIAN_FRONTEND=noninteractive

# Install selected extensions and other stuff
RUN apt-get update \
    && apt-get -y --no-install-recommends install  php-memcached php7.4-mysql php-redis php-xdebug php7.4-ldap php7.4-soap php-yaml php-zmq \
    && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*


#RUN touch /usr/local/etc/php/conf.d/xdebug.ini; \

RUN echo xdebug.remote_enable=1 >> /etc/php/7.4/fpm/conf.d/20-xdebug.ini; \
    echo xdebug.remote_autostart=1 >> /etc/php/7.4/fpm/conf.d/20-xdebug.ini; \
    echo xdebug.remote_connect_back=1 >> /etc/php/7.4/fpm/conf.d/20-xdebug.ini; \
    echo xdebug.remote_host=192.168.44.1 >> /etc/php/7.4/fpm/conf.d/20-xdebug.ini; \
    echo xdebug.remote_port=9003 >> /etc/php/7.4/fpm/conf.d/20-xdebug.ini; \
    echo xdebug.remote_log=/tmp/php5-xdebug.log >> /etc/php/7.4/fpm/conf.d/20-xdebug.ini;




# Install git
RUN apt-get update \
    && apt-get -y install git vim \
    && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*


#Install composer

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php composer-setup.php --install-dir=/usr/local/bin --filename=composer;
RUN php -r "unlink('composer-setup.php');"



RUN echo alias ls=\'ls -F --color=never\' >>~/.bashrc; \
    echo alias ll=\'ls -alF --color=never\'  >>~/.bashrc; \
    echo alias la=\'ls -AF --color=never\' >>~/.bashrc; \
    echo alias l=\'ls -F --color=never\' >>~/.bashrc; 


 
