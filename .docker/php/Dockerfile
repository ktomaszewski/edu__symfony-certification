FROM php:8.4-cli

RUN apt-get update

RUN apt-get install -y git
RUN apt-get install -y libicu-dev && docker-php-ext-configure intl && docker-php-ext-install intl
RUN docker-php-ext-install opcache
RUN pecl install xdebug && docker-php-ext-enable xdebug

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN curl -sS https://get.symfony.com/cli/installer | bash && mv /root/.symfony5/bin/symfony /usr/local/bin/symfony
RUN symfony server:ca:install

WORKDIR /usr/src
CMD ["symfony", "server:start", "--allow-all-ip"]
