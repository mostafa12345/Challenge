FROM php:8.1-fpm

# Set environment variables for database connection
ENV DB_CONNECTION=mysql
ENV DB_HOST=db
ENV DB_PORT=3306
ENV DB_DATABASE=bookapi
ENV DB_USERNAME=app
ENV DB_PASSWORD=password

# Set working directory
WORKDIR /var/www/html/api

# Install system dependencies
RUN apt-get update && apt-get install -y \
    libpng-dev \
    libjpeg62-turbo-dev \
    libfreetype6-dev \
    zip \
    unzip \
    git \
    curl \
    libzip-dev \
    && docker-php-ext-configure zip \
    && docker-php-ext-install pdo_mysql mysqli gd zip

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Copy application files
COPY . .

# Install PHP dependencies
RUN composer install --no-dev --optimize-autoloader
COPY .env .env

# Set permissions for storage and cache
RUN chown -R www-data:www-data /var/www/html/api/storage /var/www/html/api/bootstrap/cache
RUN curl -L https://github.com/jwilder/dockerize/releases/download/v0.6.1/dockerize-linux-amd64-v0.6.1.tar.gz | tar -C /usr/local/bin -xzv
# Expose port 8000
EXPOSE 8000

# Command to run the PHP application
CMD ["sh", "-c", "dockerize -wait tcp://db:3306 -timeout 60s && php artisan migrate --force && php artisan serve --host=0.0.0.0 --port=8000"]

