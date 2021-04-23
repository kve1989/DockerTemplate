FROM php:7.3-fpm
USER root

WORKDIR /var/www

RUN apt-get update && apt install -y \
	build-essential \
	libzip-dev \
	libpng-dev \
	libjpeg62-turbo-dev \
	libwebp-dev \
	libonig-dev \
	libxpm-dev \
	libfreetype6 \
	libfreetype6-dev \
	locales \
	zip \
	jpegoptim optipng pngquant gifsicle \
	vim \
	unzip \
	git \
	wget \
	curl

RUN apt-get clean && rm -rf /var/lib/apt/lists/*

RUN docker-php-ext-install pdo_mysql mysqli mbstring zip exif pcntl gd

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

RUN groupadd -g 1000 www
RUN useradd -u 1000 -ms /bin/bash -g www www

COPY ./src/ /var/www
COPY --chown=www:www ./src/ /var/www

USER www

EXPOSE 9000
CMD ["php-fpm"]