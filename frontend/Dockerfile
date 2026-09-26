# FROM nginx:1.24
# RUN rm -rf /usr/share/nginx/html/*
# RUN rm -rf /etc/nginx/nginx.conf
# RUN rm -rf /etc/nginx/conf.d/default.conf
# COPY static /usr/share/nginx/html/
# COPY nginx.conf /etc/nginx/nginx.conf
# CMD ["nginx", "-g", "daemon off;"]

FROM nginx:1.24
RUN rm -rf /usr/share/nginx/html/index.html
RUN rm -rf /etc/nginx/nginx.conf
RUN rm -rf /etc/nginx/conf.d/default.conf
ADD nginx.conf /etc/nginx/nginx.conf
ADD static /usr/share/nginx/html/