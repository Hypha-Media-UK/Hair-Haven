FROM mcr.microsoft.com/devcontainers/php:8.3

# Install system packages
RUN apt-get update && apt-get install -y \
    apache2 \
    mysql-server \
    libapache2-mod-php \
    curl \
    unzip \
    git \
    && rm -rf /var/lib/apt/lists/*

# Enable Apache mods
RUN a2enmod php8.3
RUN a2enmod rewrite

# Install PHP extensions
RUN docker-php-ext-install bcmath intl pdo_mysql

# Configure Apache document root
RUN sed -i "s|/var/www/html|/workspaces/Hair-Haven/web|g" /etc/apache2/sites-available/000-default.conf

# Start services on container start
CMD service mysql start && service apache2 start && tail -f /var/log/apache2/error.log
