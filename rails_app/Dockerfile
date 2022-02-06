FROM ruby:2.7.4-slim

RUN dpkg --configure -a

RUN apt-get update && apt-get install -qq -y --no-install-recommends \
  build-essential \
  sqlite3 \
  libsqlite3-dev

RUN mkdir -p /app
WORKDIR /app

COPY Gemfile Gemfile.lock ./
RUN gem install bundler && bundle install --jobs 4 --retry 5

COPY . .

EXPOSE 5000
