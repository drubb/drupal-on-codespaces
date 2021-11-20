FROM wodby/php:8.0
COPY php.ini /usr/local/etc/php/conf.d/
USER root
RUN apk add --update nodejs npm mc
RUN wget -O /home/wodby/vsls-reqs https://aka.ms/vsls-linux-prereq-script && chmod +x /home/wodby/vsls-reqs && /home/wodby/vsls-reqs
USER wodby
RUN composer global require drush/drush-launcher:@dev