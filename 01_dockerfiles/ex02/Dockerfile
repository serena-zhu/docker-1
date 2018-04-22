# You are going to create your first Dockerfile to containerize Rails applications. That’s
# a special configuration: this particular Dockerfile will be generic, and called in another
# Dockerfile, that will look something like this:

# FROM ft-rails:on-build
# EXPOSE 3000
# CMD ["rails", "s", "-b", "0.0.0.0", "-p", "3000"]
# rails server command: -b option binds rails to the specified IP; -p option runs rails on the specified port
# Your generic container should install, via a ruby container, all the necessary dependencies
# and gems, then copy your rails application in the /opt/app folder of your
# container. Docker has to install the approtiate gems when it builds, but also launch
# the migrations and the db population for your application. The child Dockerfile should
# launch the rails server (see example below). If you don’t know what commands to use,
# it’s high time to look at the Ruby on Rails documentation.

FROM ruby
RUN apt-get -y update && apt-get -y upgrade && apt-get install -y rails && gem install rails
ONBUILD RUN rails new my_app && cd my_app
ONBUILD RUN bundle update && bundle install
ONBUILD RUN rake db:migrate
ONBUILD ENTRYPOINT rails server

# apt-get -y update && apt-get -y upgrade && apt-get install -y rails
# rails new weblog 
# cd weblog
# rails generate scaffold post title:string body:text (dont need this step)
# rake db:migrate (for rails < 5.2) or rails db:migrate
# rails server (then go to http://localhost:3000) & (http://localhost:posts)
# 
# http://rubyonrails.org/

# http://goinbigdata.com/docker-run-vs-cmd-vs-entrypoint/