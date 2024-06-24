# FROM {{Your build image base which you build in your prevoise step}}
# Add user for laravel application
RUN groupadd -g 1000 www
RUN useradd -u 1000 -ms /bin/bash -g www www

# Copy code to /var/www
COPY --chown=www:www-data . /var/www
WORKDIR /var/www

# add root to www group
RUN chmod 777 -R /var/www/storage

# PHP Error Log Files
RUN mkdir /var/log/php
RUN touch /var/log/php/errors.log && chmod 777 /var/log/php/errors.log
# RUN composer diagnose
RUN echo '{}' > ~/.composer/composer.json
RUN  composer update -vvv --optimize-autoloader 
RUN chmod +x /var/www/docker/run.sh

RUN cd /var/www

# php artisan migrate:fresh --seed
RUN php artisan cache:clear
RUN php artisan route:cache

EXPOSE 80

