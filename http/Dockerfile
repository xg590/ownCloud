FROM ubuntu:18.04
ENV TZ=Europe/Amsterdam 
# America/New_York
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN apt update 
RUN apt install -y apache2 wget    \
                   php7.2-gd       \
                   php7.2-xml      \
                   php7.2-zip      \
                   php7.2-intl     \
                   php7.2-curl     \
                   php7.2-mysql    \
                   php7.2-imagick  \
                   php7.2-mbstring \
                   libapache2-mod-php7.2
#                  Choosing php7.2 is because of owncloud since it isn't compatible with php7.4 (the latest)
RUN rm -rf /var/lib/apt/lists/*
RUN a2enmod ssl
COPY 000-default.conf /etc/apache2/sites-enabled/000-default.conf 
CMD ["apachectl", "-D", "FOREGROUND"]
