FROM httpd:latest

ENV APACHE_CONF_DIR=/usr/local/apache2/conf
COPY apache-selfsigned.crt ${APACHE_CONF_DIR}/apache-selfsigned.crt
COPY apache-selfsigned.key ${APACHE_CONF_DIR}/apache-selfsigned.key