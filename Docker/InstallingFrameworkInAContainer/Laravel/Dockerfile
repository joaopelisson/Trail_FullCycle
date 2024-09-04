# Install PHP 7.4 in a container
FROM php:7.4-cli

# Set the working directory
WORKDIR /var/www

# Install the zip extension
RUN apt-get update \
    && apt-get install -y libzip-dev \
    && docker-php-ext-install zip

# Install Composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && \
    php composer-setup.php --install-dir=/usr/local/bin --filename=composer && \
    php -r "unlink('composer-setup.php');"

# Install Laravel
RUN composer create-project --prefer-dist laravel/laravel laravel

# Set the entrypoint to run the Laravel development server
ENTRYPOINT [ "php", "laravel/artisan", "serve" ]

# Set the default command
CMD [ "--host=0.0.0.0" ]