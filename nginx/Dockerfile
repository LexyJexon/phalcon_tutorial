# Используем официальный образ Nginx
FROM nginx:latest

# Копируем конфигурацию Nginx
COPY ./nginx/nginx.conf /etc/nginx/conf.d/default.conf

# Настраиваем рабочую директорию
WORKDIR /var/www/html/public

# Открываем порт
EXPOSE 8080

