FROM dunglas/frankenphp
# Instalar dependências do sistema e Composer
RUN apt-get update && apt-get install -y \
    git \
    unzip \
    zip \
    curl \
    libzip-dev \
    libicu-dev \
    libpq-dev \
    libonig-dev \
    libxml2-dev \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    && docker-php-ext-configure intl \
    && docker-php-ext-install intl zip pdo pdo_mysql \
    && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Criar manualmente o diretório global do Composer e garantir permissões
RUN mkdir -p /root/.composer && chmod -R 755 /root/.composer

# Configurar variáveis de ambiente para garantir o PATH correto
ENV COMPOSER_HOME="/root/.composer"
ENV PATH="${COMPOSER_HOME}/vendor/bin:${PATH}"

# Instalar o Laravel Installer globalmente
RUN /usr/local/bin/composer global require laravel/installer --prefer-dist --no-progress --no-suggest --optimize-autoloader || \
    (cat /root/.composer/composer.log && exit 1)

# Limpar cache para reduzir o tamanho da imagem
RUN apt-get clean && rm -rf /var/lib/apt/lists/*