# Docker can be useful to test an application that’s still being developed without polluting
# your libraries. You will have to design a Dockerfile that gets the development
# version of Gitlab - Community Edition installs it with all the dependencies and the necessary
# configurations, and launches the application, all as it builds. The container will be
# deemed valid if you can access the web client, create users and interact via GIT with this
# container (HTTPS and SSH). Obviously, you are not allowed to use the official container
# from Gitlab, it would be a shame...

#FROM gitlab/gitlab-runner:latest

FROM ubuntu:16.04
RUN apt-get update && apt-get -y upgrade
RUN apt-get install -y curl openssh-server ca-certificates git

# Basically, git clone the development branch of gitlab 
# Should be something like:
# git clone -b develop https://github.com/gitlabhq/gitlabhq


RUN curl -sS https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | bash
RUN apt-get install gitlab-ce
RUN gitlab-ctl reconfigure

EXPOSE 9000


#RUN curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ee/script.deb.sh | bash
# RUN EXTERNAL_URL="http://localhost:9000" apt-get install gitlab-ee


# https://about.gitlab.com/installation/#debian

