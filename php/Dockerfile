FROM php:8.2-fpm-alpine

# Set the working directory to /var/www/html
WORKDIR /var/www/html
# Install any needed extensions
RUN docker-php-ext-install pdo pdo_mysql
# Install Composer globally
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer | sudo mv composer.phar /usr/bin/composer
# Install Supervisor for process control
#RUN apt-get update && apt-get install -y supervisor && \
    #mkdir -p /var/log/supervisor
# Copy the application code into the container
COPY . /var/www/html
# Run Composer install
RUN composer install
# Copy the Laravel worker configuration
COPY ./worker.conf /etc/supervisor/conf.d/
# Start Supervisor to manage the Laravel worker process
CMD ["/usr/bin/supervisord", "-n"]























#RUN apt update \
    #&& apt install -y zlib1g-dev g++ git libicu-dev zip libzip-dev zip \
    #&& docker-php-ext-install intl opcache pdo pdo_mysql \
    #&& pecl install apcu \
    #&& docker-php-ext-enable apcu \
    #""&& docker-php-ext-configure zip \
    #&& docker-php-ext-install zip


#WORKDIR /var/www/symfony_docker

# install cron
#RUN apt-get update && apt-get install -y cron
#COPY ./scheduled-subscription-charges.crontab /etc/cron.d/tasks-crontab
#RUN touch /var/log/cron.log
#RUN chmod 0644 /etc/cron.d/tasks-crontab &&\
#    crontab /etc/cron.d/tasks-crontab


#end install cron

#RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

#RUN curl -sS https://get.symfony.com/cli/installer | bash
#RUN mv /root/.symfony5/bin/symfony /usr/local/bin/symfony
#RUN git config --global user.email "kammegnealex@gmail.com" \
    #&& git config --global user.name "Kammegne Djoum Alex"

#run the cron tasks
#RUN cron

