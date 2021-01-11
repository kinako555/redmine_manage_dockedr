FROM ruby:2.6.5
RUN apt-get update -qq && apt-get install -y build-essential \ 
                       libpq-dev \        
                       nodejs
RUN mkdir /redmine
WORKDIR /redmine
COPY . /redmine
RUN gem install bundler && bundle install