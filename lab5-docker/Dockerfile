FROM debian
ADD debian.list /etc/apt/sources.list.d/
RUN apt-get -y update && apt-get -y upgrade && apt-get -y install nginx && apt-get clean && \
    cd /var/www/ && rm -rf ./* && \
    mkdir -p asya.com/img && \
    chmod -R 754 /var/www/asya.com/ && \
    useradd Asya && groupadd Kozina && usermod -aG Kozina Asya && \
    chown -R Asya:Kozina /var/www/asya.com/ && \
    sed -i 's/\/var\/www\/html/\/var\/www\/asya.com/g' /etc/nginx/sites-enabled/default && \
    sed -i 's/user www-data/user Asya/g' /etc/nginx/nginx.conf
ADD index.html /var/www/asya.com/
ADD img.jpg /var/www/asya.com/img/
CMD ["nginx", "-g", "daemon off;"]