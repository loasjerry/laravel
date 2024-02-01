# Use a base image with PHP and Nginx
FROM php:8.2-fpm

# Set the working directory inside the container
WORKDIR /var/www/html

# Copy the project files into the container
COPY . .

# Install system dependencies
RUN apt-get update && \
    apt-get install -y \
        nginx \
        libzip-dev \
        zip \
        unzip && \
    docker-php-ext-install pdo_mysql zip

# Configure Nginx
COPY nginx.conf /etc/nginx/sites-available/default
RUN ln -s /etc/nginx/sites-available/default /etc/nginx/sites-enabled/default

# Set the appropriate permissions
RUN chown -R www-data:www-data /var/www/html && \
    chmod -R 755 /var/www/html/storage && \
    chmod -R 755 /var/www/html/bootstrap/cache

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Install project dependencies
RUN composer install --optimize-autoloader --no-dev

# Expose port 80 for Nginx
EXPOSE 80

# Define the command to start PHP-FPM and Nginx
CMD service php8.2-fpm start && nginx -g "daemon off;"
