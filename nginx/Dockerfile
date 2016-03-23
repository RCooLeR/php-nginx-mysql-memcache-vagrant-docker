FROM nginx:latest

COPY ./conf/nginx.conf /etc/nginx/nginx.conf
COPY ./conf/app.conf /etc/nginx/sites-available/app.conf
RUN  mkdir /etc/nginx/sites-enabled
RUN  ln -s /etc/nginx/sites-available/app.conf /etc/nginx/sites-enabled/app.conf
