# mysql/Dockerfile
FROM ubuntu:latest

# MySQLサーバーをインストール
RUN apt-get update -qq && apt-get install -y mysql-server

# MySQL設定の修正
RUN sed -i 's/bind-address\s*=\s*127.0.0.1/bind-address = 0.0.0.0/' /etc/mysql/mysql.conf.d/mysqld.cnf

# ポートを公開
EXPOSE 3306

# MySQLサーバーを起動
CMD ["mysqld"]
