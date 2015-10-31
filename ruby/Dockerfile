FROM ruby:2.2.0
MAINTAINER Tsuyoshi Ushio <ushio@simplearchitect.com>

# Development tools and sqlite3
RUN apt-get update -qq && apt-get install -y build-essential
RUN apt-get install -y libsqlite3-dev sqlite3

# for nokogiri
RUN apt-get install -y libxml2-dev libxslt1-dev

# node.js installation

RUN apt-get update
RUN curl --silent --location https://deb.nodesource.com/setup_0.12 | bash -
RUN apt-get install -y nodejs
RUN apt-get install -y git cmake

# vsoagent-installer

RUN npm install -g vsoagent-installer grunt bower grunt-cli jake yo gulp grunt-cli

# nokogiri

RUN apt-get install -y libxml2-dev libxslt1-dev

# capybara-webkit

RUN apt-get install -y libqt4-webkit libqt4-dev xvfb

# Create a service user
RUN echo "vsoservice\nvsoservice\n\n\n\n\n\n\n" | adduser vsoservice
RUN su vsoservice

# Install agent
RUN mkdir /opt/vsoagent
RUN mkdir /opt/vsoagent/_work
WORKDIR /opt/vsoagent
RUN vsoagent-installer
WORKDIR /opt/vsoagent/agent
COPY agent.config /opt/vsoagent/.agent
RUN chown -R vsoservice /opt/vsoagent
RUN chown -R vsoservice /usr/local/bundle

USER vsoservice
ENTRYPOINT /bin/bash
