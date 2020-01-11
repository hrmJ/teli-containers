FROM nginx

RUN mkdir /wwwroot
COPY containers/telinginx/nginx.conf /etc/nginx/nginx.conf
#RUN CHOWN nginx:nginx -R /user/share/nginx/html
RUN service nginx start
