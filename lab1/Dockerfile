FROM alpine:latest

RUN apk update && apk add --no-cache nginx && \
    mkdir -p /run/nginx && \
    chown -R nginx:nginx /var/lib/nginx && \
    chown -R nginx:nginx /etc/nginx && \
    chown -R nginx:nginx /var/www

COPY nginx.conf /etc/nginx/nginx.conf

USER nginx

EXPOSE 8080

CMD ["nginx", "-g", "daemon off;"]