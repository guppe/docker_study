FROM ubuntu:latest

# Apacheをインストール
RUN apt-get update -qq && apt-get install -y apache2

# 必要なモジュールを有効化
RUN a2enmod proxy
RUN a2enmod proxy_http

# 仮想ホストの設定
RUN echo '<VirtualHost *:80>\n\
    ServerName localhost\n\
    ProxyPass / http://web:3000/\n\
    ProxyPassReverse / http://web:3000/\n\
    </VirtualHost>' > /etc/apache2/sites-available/000-default.conf

# ポートを公開
EXPOSE 80

# Apacheサーバーを起動
CMD ["apachectl", "-D", "FOREGROUND"]
