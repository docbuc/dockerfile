# Datei Dockerfile
FROM ubuntu:20.04

LABEL maintainer "name@somehost.com"
LABEL description "Test"

# Umgebungsvariablen und Zeitzone einstellen 
# (erspart interaktive Rückfragen)
ENV TZ="Europe/Berlin" \
    APACHE_RUN_USER=www-data \
    APACHE_RUN_GROUP=www-data \
    APACHE_LOG_DIR=/var/log/apache2

# Apache installieren, unnötige Dateien aus dem Paket-Cache
# gleich wieder entfernen, HTTPS aktivieren
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && \
    echo $TZ > /etc/timezone && \
    apt-get update && \
    apt-get install -y apache2 && \
    apt-get -y clean && \
    rm -r /var/cache/apt /var/lib/apt/lists/* && \
    a2ensite default-ssl && \
    a2enmod ssl

EXPOSE 80 443

# gesamten Inhalt des Projektverzeichnisses
# samplesite nach /var/www/html kopieren
COPY samplesite/ /var/www/html

CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
