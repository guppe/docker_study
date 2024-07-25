FROM ubuntu:latest

# 必要なパッケージをインストール
RUN apt-get update -qq && apt-get install -y \
    build-essential \
    libpq-dev \
    nodejs \
    curl \
    gnupg \
    libssl-dev \
    libreadline-dev \
    zlib1g-dev \
    mysql-client \
    git

# Rubyをインストール
RUN apt-get install -y ruby-full

# Bundlerをインストール
RUN gem install bundler

# 作業ディレクトリを作成
RUN mkdir /myapp
WORKDIR /myapp

# Railsをインストール
RUN gem install rails

# Railsプロジェクトを作成
RUN rails new . --force --database=mysql

# ポートを公開
EXPOSE 3000

# Railsサーバーを起動
CMD ["rails", "server", "-b", "0.0.0.0"]
