FROM ruby
RUN apt-get update && apt-get upgrade -y
RUN apt-get install gem -y
RUN apt-get install sqlite3 build-essential nodejs -y
RUN gem install rails
COPY app/ /opt/app
WORKDIR /opt/app
RUN bundle install
ONBUILD RUN rake db:migrate
ONBUILD RUN rake db:seed
