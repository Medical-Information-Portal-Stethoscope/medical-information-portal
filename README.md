# medical-information-portal


cd infra/prod/data/nginx/ssl
openssl req -x509 -nodes -days 3650 -newkey rsa:2048 -keyout ./nginx.key -out ./nginx.crt
