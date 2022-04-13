FROM nextcloud:fpm-alpine
RUN apk add ghostscript imagemagick imagemagick-dev
RUN pecl install imagick; exit 0
RUN docker-php-ext-enable imagick