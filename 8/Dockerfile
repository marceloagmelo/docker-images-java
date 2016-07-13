FROM ubuntu:12.04

MAINTAINER Marcela Melo <marceloagmelo@gmail.com>

RUN (echo "deb http://archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse" > /etc/apt/sources.list && echo "deb http://archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse" >> /etc/apt/sources.list && echo "deb http://archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse" >> /etc/apt/sources.list && echo "deb http://archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse" >> /etc/apt/sources.list)

RUN echo "root:Docker!" | chpasswd

RUN apt-get update

# install prereqs
RUN apt-get install -y build-essential vim sudo wget net-tools telnet iputils-ping curl unzip bzip2

# java 8
RUN (curl -L -k -b "oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u72-b15/server-jre-8u72-linux-x64.tar.gz | gunzip -c | tar x) \
 && mv /jdk1.8.0_72 /jdk

ENV JAVA_HOME /jdk
ENV JRE_HOME  $JAVA_HOME/jre
ENV PATH $PATH:$JAVA_HOME/bin
