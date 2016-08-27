FROM ubuntu:14.04

MAINTAINER sinha.ksaurabh@gmail.com

ENV HTTPD_PREFIX /etc/apache2

#Run the update
RUN apt-get update

#Install the Different Components Required
RUN apt-get install -y \
    apache2 \
    curl \
    git \
    php5 \
    libapache2-mod-php5 \
    php5-cli \
    php5-curl \
    php5-json \
    php5-mcrypt \
    php5-mysql \
    php5-gd \
    && php5enmod mcrypt \
    && apt-get clean

# Install extra utils
RUN curl -sS https://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer \
    && chmod a+x /usr/local/bin/composer

#Expose the Port for this service
EXPOSE 80

RUN ln -s $HTTPD_PREFIX/mods-available/expires.load $HTTPD_PREFIX/mods-enabled/expires.load \
    && ln -s $HTTPD_PREFIX/mods-available/headers.load $HTTPD_PREFIX/mods-enabled/headers.load \
	&& ln -s $HTTPD_PREFIX/mods-available/rewrite.load $HTTPD_PREFIX/mods-enabled/rewrite.load

#Run the Initial Command Required
RUN service apache2 start

#Create the Directory required for the Apache Document Root
RUN mkdir /var/www/html/public

#Add the Apache Configuration file
ADD ./setup.conf /etc/apache2/sites-available/000-default.conf

#Restart Apache2 Server
RUN service apache2 restart

WORKDIR /var/www/html/public

CMD /usr/sbin/apache2ctl -D FOREGROUND
