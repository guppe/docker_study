FROM ubuntu:latest
ARG RUBYGEMS_VERSION=3.3.20

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
    git \
    libxml2-dev \
    libxslt1-dev \
    libcurl4-openssl-dev \
    libyaml-dev \
    software-properties-common

# Rubyをインストール
RUN apt-get install -y ruby-full

# Bundlerをインストール
RUN gem install bundler

# 作業ディレクトリを作成
RUN mkdir /myapp
WORKDIR /myapp

# GemfileとGemfile.lockをコピー
COPY Gemfile /myapp/Gemfile
COPY Gemfile.lock /myapp/Gemfile.lock

# Bundlerを実行
RUN bundle update
RUN bundle install

# ソースコードをコピー
COPY . /docker_study

# ポートを公開
EXPOSE 3000

# Railsサーバーを起動
CMD ["rails", "server", "-b", "0.0.0.0"]
