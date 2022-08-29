FROM php:8.1-fpm

# nvm environment variables
ENV NVM_DIR /usr/local/nvm
ENV NVM_VERSION 0.39.1
ENV NODE_VERSION 16.17.0
ENV NODE_PATH $NVM_DIR/v$NODE_VERSION/lib/node_modules
ENV PATH $NVM_DIR/versions/node/v$NODE_VERSION/bin:$PATH

RUN rm /bin/sh && ln -s /bin/bash /bin/sh

# Install system dependencies
RUN apt-get update && \
    apt-get install -y \
        libmcrypt-dev mariadb-client git \
        curl \
        libzip-dev \
        libpng-dev \
        libonig-dev \
        libxml2-dev \
        zip \
        unzip \
        libmcrypt-dev \
        python3 \
        python3-pip

# Install PHP extensions
RUN docker-php-ext-install pdo_mysql mbstring exif pcntl bcmath gd zip && \
    pecl install mcrypt-1.0.5 redis && \
    docker-php-ext-enable mcrypt redis && \
    docker-php-ext-configure pdo_mysql && \
    docker-php-ext-install pdo_mysql

# Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Get latest Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Create system user to run Composer and Artisan Commands
RUN useradd -G www-data,root -u 1000 -d /home/rzerostern rzerostern
RUN mkdir -p /home/rzerostern/.composer && mkdir -p /usr/local/nvm && \
    chown -R rzerostern:rzerostern /home/rzerostern

# Optional: Install Python dependencies

# install nvm
# https://github.com/creationix/nvm#install-script
RUN curl -o- https://raw.githubusercontent.com/creationix/nvm/v$NVM_VERSION/install.sh | bash

# install NodeJS and NPM
RUN source $NVM_DIR/nvm.sh \
    && nvm install $NODE_VERSION \
    && nvm alias default $NODE_VERSION \
    && nvm use default

# confirm installation
RUN node -v
RUN npm -v

# Set working directory
WORKDIR /var/www

USER $user