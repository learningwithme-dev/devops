FROM nginx:stable-alpine
COPY ssl  /etc/nginx/ssl
COPY static  /static
COPY nginx.conf  /etc/nginx/
COPY node/generated  /etc/nginx/conf.d/
COPY reverse_proxy/api  /etc/nginx/conf.d/
COPY reverse_proxy/standard  /etc/nginx/conf.d/standard
COPY reverse_proxy/custom  /etc/nginx/conf.d/custom
