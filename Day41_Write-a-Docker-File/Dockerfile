# Use Ubuntu 24.04 as base image
FROM ubuntu:24.04

# Install apache2
RUN apt-get update && \
    apt-get install -y apache2 && \
    apt-get clean

# Change Apache to listen on port 8086
RUN sed -i 's/Listen 80/Listen 8086/' /etc/apache2/ports.conf && \
    sed -i 's/<VirtualHost \*:80>/<VirtualHost *:8086>/' /etc/apache2/sites-available/000-default.conf

# Expose port 8086
EXPOSE 8086

# Run apache2 in foreground
CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]

