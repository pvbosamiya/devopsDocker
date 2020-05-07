FROM ruby:2.6.0

WORKDIR /mydir
RUN apt-get update && apt-get install -y curl
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash -
RUN apt-get install -y nodejs
RUN /usr/bin/node -v && /usr/bin/npm -v

RUN gem install bundler

COPY rails-example-project .
RUN bundle install

ENV RAILS_ENV=production
ENV RAILS_LOG_TO_STDOUT=true
ENV SECRET_KEY_BASE='/bin/rake secret'

EXPOSE 3000

RUN rails credentials:edit
RUN rails db:migrate
RUN rake assets:precompile
ENTRYPOINT [ "rails", "s", "-e", "production" ]