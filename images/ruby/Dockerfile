FROM circleci/ruby:2.4.7-node AS ruby

ENV WORKDIR /home/circleci
WORKDIR $WORKDIR
RUN mkdir tmp bin && sudo apt-get update
ENV PATH $PATH:$WORKDIR/bin

# Install CodeClimate Test Reporter
RUN wget -qO bin/cc-test-reporter https://codeclimate.com/downloads/test-reporter/test-reporter-0.6.3-linux-amd64 \
  && chmod u+x bin/cc-test-reporter

# Install Elasticsearch
RUN wget -qO tmp/elasticsearch.tar.gz https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-6.2.4.tar.gz \
  && tar -xf tmp/elasticsearch.tar.gz
ENV TEST_CLUSTER_COMMAND $WORKDIR/elasticsearch-6.2.4/bin/elasticsearch
ENV PATH $PATH:$WORKDIR/elasticsearch-6.2.4/bin

# Install Image Magick
RUN sudo apt-get install libfftw3-double3 \
  && sudo apt-get install --only-upgrade imagemagick

# Install Java
RUN wget -qO tmp/openjdk.tar.gz https://download.java.net/java/GA/jdk11/13/GPL/openjdk-11.0.1_linux-x64_bin.tar.gz \
  && tar -xf tmp/openjdk.tar.gz
 ENV JAVA_HOME $WORKDIR/jdk-11.0.1
ENV PATH $PATH:$JAVA_HOME/bin

# Install X-Pack Elasticsearch Plugin
RUN elasticsearch-plugin install x-pack

RUN sudo apt-get clean && rm -Rf tmp
