FROM php:8.2.0-fpm-bullseye

# Обновление списка пакетов и установка зависимостей
RUN apt-get update && apt-get install -y \
    libpq-dev \
    git \
    unzip \
    zip
  #  libcurl4-openssl-dev \
  #  libxml2-dev \
  #  libonig-dev \
  #  libxslt1-dev \
  #  libzip-dev \
  #  libicu-dev \
  #  default-mysql-client

# Установим nvm
  ENV NVM_DIR /root/.nvm
  RUN curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash

# Установим Node.js версии 18 с помощью nvm
  RUN bash -c "source $NVM_DIR/nvm.sh && nvm install 18 && nvm alias default 18 && nvm use default"

# Обновим переменные окружения для nvm и node
  ENV NODE_VERSION 18
  ENV PATH $NVM_DIR/versions/node/v$NODE_VERSION/bin:$PATH

# Установим npm и yarn
  RUN bash -c "source $NVM_DIR/nvm.sh && npm install -g npm && npm install -g yarn"

# Установка PHP-расширений по одному, для отслеживания возможных ошибокdcd -
  # ctype - по умолчанию
  # curl - по умолчанию
  # dom - по умолчанию
  # fileinfo - по умолчанию
  # filter - по умолчанию
  # hash - по умолчанию
  # mbstring - по умолчанию
  # openssl - по умолчанию
  # pcre - по умолчанию
  # PDO - по умолчанию
  # session - по умолчанию
  # tokenizer - по умолчанию
  # xml - по умолчанию

RUN docker-php-ext-install pdo_pgsql

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Очистка кэша apt
RUN apt-get clean && rm -rf /var/lib/apt/lists/*
