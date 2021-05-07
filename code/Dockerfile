FROM ubuntu:16.04

ARG JMETER_VERSION="-5.2.1"
ARG JAVA_VERSION="1.8.0_292"

# Install java
RUN apt-get update \
	&& apt-get install openjdk-8-jdk curl unzip -y \
	&& java -version \
#	&& java update-alternatives --set java /usr/lib/jvm/jdk${JAVA_VERSION}/bin/java \
	&& java -version

# Install jmeter
RUN curl -L --silent https://archive.apache.org/dist/jmeter/binaries/apache-jmeter${JMETER_VERSION}.tgz > apache-jmeter${JMETER_VERSION}.tgz
RUN tar -xzf apache-jmeter${JMETER_VERSION}.tgz 

# Settings
ENV PATH $PATH:/apache-jmeter${JMETER_VERSION}/bin

# Copy all code inside the container
COPY * /

# Create a folder to save the jmeter results
RUN mkdir /results

# Working Directory
WORKDIR /apache-jmeter${JMETER_VERSION}

ENTRYPOINT ["/launch.sh"]