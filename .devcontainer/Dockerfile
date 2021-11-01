FROM wodby/php:8.0
COPY php.ini /usr/local/etc/php/conf.d/
USER root
RUN apk add --update nodejs npm mc
USER wodby
RUN composer global require drush/drush-launcher:@dev