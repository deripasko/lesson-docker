FROM php:7.2-fpm

MAINTAINER Ivan Klimchuk <ivan@klimchuk.com> (@alroniks)

RUN apt-get update && apt-get install -y curl zip unzip git vim

RUN docker-php-ext-install pdo pdo_mysql zip

RUN php -r "readfile('http://getcomposer.org/installer');" | php -- --install-dir=/usr/bin/ --filename=composer

RUN cd /var/www && git clone https://github.com/modmore/gitify.git && cd Gitify && composer install && cd -

RUN { echo 'date.timezone=Europe/Minsk'; } > /usr/local/etc/php/conf.d/datetime.ini

WORKDIR /var/www/html/public

VOLUME /var/www/html/public

RUN usermod -u 1000 www-data

EXPOSE 9000

CMD ["php-fpm"]
