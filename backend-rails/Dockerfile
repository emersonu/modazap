# Use a imagem oficial do Ruby
FROM ruby:3.3.5-slim

ENV BUNDLER_VERSION=2.5.23

# Instale dependências do sistema
RUN apt-get update -qq && apt-get install -y build-essential libpq-dev

RUN gem install bundler -v "$BUNDLER_VERSION"

# Defina o diretório de trabalho no container
WORKDIR /app

# Copie o Gemfile e o Gemfile.lock para o container
COPY Gemfile Gemfile.lock ./

# Instale as gems
RUN bundle _${BUNDLER_VERSION}_ install

# Copie o restante do código do projeto
COPY . .

# Exponha a porta padrão do Rails
EXPOSE 3000

# Comando para iniciar o servidor Rails
CMD ["rails", "server", "-b", "0.0.0.0"]