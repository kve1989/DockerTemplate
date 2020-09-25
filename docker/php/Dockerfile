FROM php:7.3-fpm

USER root

WORKDIR /var/www

RUN apt-get update && apt install -y \
	build-essential \
	libzip-dev \
	libpng-dev \
	libjpeg62-turbo-dev \
	libwebp-dev \
	libxpm-dev \
	libfreetype6 \
	libfreetype6-dev \
	locales \
	zip \
	jpegoptim optipng pngquant gifsicle \
	vim \
	unzip \
	git \
	curl

RUN apt-get clean && rm -rf /var/lib/apt/lists/*

RUN docker-php-ext-install pdo_mysql mbstring zip exif pcntl
RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include --with-webp-dir=/usr/include --with-jpeg-dir=/usr/include

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

COPY ./src/ /var/www

USER www-data

EXPOSE 9000
CMD ["php-fpm"]