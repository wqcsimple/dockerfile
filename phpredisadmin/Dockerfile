FROM composer/composer

RUN mkdir -p /src/app && cd /src/app && git clone https://github.com/erikdubbelboer/phpRedisAdmin.git .
WORKDIR /src/app

COPY includes/config.sample.inc.php /src/app/includes/config.sample.inc.php

RUN composer install

EXPOSE 80

ENTRYPOINT [ "php", "-S", "0.0.0.0:80" ]
