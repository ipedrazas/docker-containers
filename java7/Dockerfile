FROM ubuntu:latest

MAINTAINER Ivan Pedrazas <ivan@pedrazas.me>

RUN sed 's/main$/main universe/' -i /etc/apt/sources.list
RUN apt-get update && apt-get install -y software-properties-common python-software-properties
RUN add-apt-repository ppa:webupd8team/java -y

RUN apt-get update
RUN echo oracle-java7-installer shared/accepted-oracle-license-v1-1 select true | /usr/bin/debconf-set-selections

RUN apt-get install -y oracle-java7-installer

RUN update-alternatives --display java

# set the java environment variables for when you "bash -l"
RUN apt-get -y install oracle-java7-set-default && apt-get clean

# set the JAVA_HOME explicitly
ENV JAVA_HOME /usr/lib/jvm/java-7-oracle