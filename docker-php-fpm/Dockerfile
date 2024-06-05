FROM php:8.2-fpm

RUN apt-get update && apt-get install -y \
		libfreetype-dev \
		libjpeg62-turbo-dev \
		libpng-dev \
	&& docker-php-ext-configure gd --with-freetype --with-jpeg \
	&& docker-php-ext-install -j$(nproc) gd

COPY --from=composer /usr/bin/composer /usr/bin/composer

#RUN mkdir /var/www

WORKDIR /var/www

#COPY lab200_app /var/www/lab200_app

# Thiết lập quyền truy cập
RUN chown -R www-data:www-data /var/www

EXPOSE 9000
CMD ["php-fpm"]