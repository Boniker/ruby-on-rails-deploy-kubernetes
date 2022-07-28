FROM ruby:2.7.2
RUN apt-get update -qq && apt-get install -y postgresql-client && apt install -y nodejs
WORKDIR /myapp
# ENV RAILS_ENV=production

ADD Gemfile /myapp/Gemfile
RUN gem install bundler -v 1.16.1
RUN bundle install
ADD . /myapp

# Add a script to be executed every time the container starts.
COPY entrypoint.sh /usr/bin/
RUN chmod +x /usr/bin/entrypoint.sh
ENTRYPOINT ["entrypoint.sh"]
EXPOSE 3000

# Start the main process.
CMD ["rails", "server", "-b", "0.0.0.0"]
