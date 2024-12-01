# Используем официальный PHP образ с FPM на базе Alpine
FROM mileschou/phalcon:8.0-fpm-alpine

# Устанавливаем необходимые утилиты и зависимости
RUN apk update && apk add --no-cache \
    bash \
    nano \
    wget \
    git \
    unzip \
    net-tools \
    libjpeg-turbo-dev \
    libpng-dev \
    freetype-dev \
    imagemagick-dev \
    gettext-dev \
    curl-dev \
    postgresql-dev \
    oniguruma-dev \
    libmemcached-dev \
    autoconf \
    g++ \
    make \
    && docker-php-ext-install -j$(nproc) \
    curl \
    fileinfo \
    pdo \
    pdo_mysql \
    mbstring \
    gd \
    opcache \
    && pecl install imagick memcached \
    && docker-php-ext-enable imagick memcached

# Устанавливаем Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Устанавливаем Phalcon DevTools
RUN git clone https://github.com/phalcon/phalcon-devtools.git /opt/phalcon-devtools && \
    ln -s /opt/phalcon-devtools/phalcon /usr/local/bin/phalcon && \
    chmod +x /usr/local/bin/phalcon

# Настраиваем рабочую директорию
WORKDIR /var/www/html

# Копируем исходный код
#COPY ./src /var/www/html

# Указываем пользователя
RUN chown -R www-data:www-data /var/www/html

# Открываем порт
EXPOSE 9000

# Стартуем PHP-FPM
CMD ["php-fpm"]

