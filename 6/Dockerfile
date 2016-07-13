FROM ubuntu:12.04

MAINTAINER Marcelo Melo <marceloagmelo@gmail.com>

RUN (echo "deb http://archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse" > /etc/apt/sources.list && echo "deb http://archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse" >> /etc/apt/sources.list && echo "deb http://archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse" >> /etc/apt/sources.list && echo "deb http://archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse" >> /etc/apt/sources.list)

RUN echo "root:Docker!" | chpasswd

RUN apt-get update

# install prereqs
RUN apt-get install -y build-essential vim sudo wget net-tools telnet iputils-ping curl unzip bzip2

ENV DOWNLOAD_DIR /tmp/downloads

RUN mkdir -p "${DOWNLOAD_DIR}"

# Install Oracle Java 6 SDK
ENV JAVA_VERSION=jdk1.6.0_45
ENV JAVA_HOME=/opt/java/${JAVA_VERSION}
ENV JDK_FILE=jdk-6u45-linux-x64.bin

# Install Java SDK
RUN wget -q --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" -O "${DOWNLOAD_DIR}/${JDK_FILE}" "http://download.oracle.com/otn-pub/java/jdk/6u45-b06/${JDK_FILE}" && \
	mkdir -p /opt/java && \
	chmod +x ${DOWNLOAD_DIR}/${JDK_FILE} && \
	${DOWNLOAD_DIR}/${JDK_FILE} && \
	mv ${JAVA_VERSION} /opt/java && \
	update-alternatives --install /usr/bin/java java /opt/java/${JAVA_VERSION}/bin/java 100 && \
	update-alternatives --config java && \
	rm -rf ${DOWNLOAD_DIR}*
