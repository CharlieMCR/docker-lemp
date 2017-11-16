FROM nginx

RUN apt-get update \
    && apt-get install -y \
     libgd-dev

ADD nginx.conf /etc/nginx/

CMD ["nginx"]

EXPOSE 80 443