# Базовый образ - alpine
FROM alpine:latest

# Установка nginx и создание пользователя
RUN apk add --no-cache nginx \
    && adduser -D -g 'www' www \
    && mkdir -p /var/www/html \
    && chown -R www:www /var/www/html \
    && mkdir -p /etc/nginx/conf.d \
    && chown -R www:www /etc/nginx/conf.d

# Копируем конфигурацию nginx в контейнер
COPY nginx.conf /etc/nginx/nginx.conf

# Запуск контейнера от пользователя www
USER www

# Открываем порт
EXPOSE 8080

# Команда запуска nginx
CMD ["nginx", "-g", "daemon off;"]