FROM php:8.3.8-fpm

# Arguments defined in docker-compose.yml
ARG USER
ARG UID

# Install system dependencies
RUN apt-get update && apt install -y  \
    curl \
    git \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    zip \
    unzip

# Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Install PHP extensions
RUN docker-php-ext-install pdo_mysql mbstring xml

RUN pecl install redis && docker-php-ext-enable redis

# Get latest Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Create system user to run Composer and Artisan Commands
RUN useradd -G www-data,root -u $UID -d /home/$USER $USER
RUN mkdir -p /home/$USER/.composer && chown -R $USER:$USER /home/$USER

# Set working directory
WORKDIR /var/www/html

USER $USER
