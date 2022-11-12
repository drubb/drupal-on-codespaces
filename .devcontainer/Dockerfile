FROM debian:bullseye-slim
ARG DEBIAN_FRONTEND=noninteractive
USER root
COPY php.ini /tmp
RUN apt-get update -yq \
    # Add updated php sources
    && apt-get install curl -yq \
    && curl -sSL https://packages.sury.org/php/README.txt | bash -x \
    # Install some common packages
    && apt-get install git imagemagick nano openssh-server sqlite3 wget unzip -yq \
    && sed -i 's/<policy domain="coder" rights="none" pattern="PDF" \/>/<policy domain="coder" rights="read|write" pattern="PDF" \/>/g' /etc/ImageMagick-6/policy.xml \
    # Install PHP CLI with some extensions for Drupal development
    && apt-get install php-cli php-apcu php-curl php-gd php-imagick php-mbstring php-sqlite3 php-zip -yq \
    && apt-get install php-pear php-dev -yq \
    && pear config-set php_ini /etc/php/8.1/cli/php.ini \
    && pecl install xdebug \
    && cat /tmp/php.ini >> /etc/php/8.1/cli/php.ini \
    # Install NodeJS LTS
    && curl -sL https://deb.nodesource.com/setup_lts.x | bash \
    && apt-get install nodejs -yq \
    # Install Composer
    && wget https://getcomposer.org/installer \
    && php installer --install-dir=/usr/local/bin --filename=composer \
    # Install global Drush launcher
    && wget -O /usr/local/bin/drush https://github.com/drush-ops/drush-launcher/releases/latest/download/drush.phar \
    && chmod +x /usr/local/bin/drush \
    # Clean up some things
    && rm installer /tmp/php.ini \
    && rm -rf /var/lib/apt/lists/* \
    # Create a user
    && useradd -m drupal -p drupal
USER drupal
ENV SHELL /bin/bash
