## Dockerfile to build Java7

# Pull base image.
FROM ubuntu:14.04

# Install.
RUN \
      sed -i 's/# \(.*multiverse$\)/\1/g' /etc/apt/sources.list && \
      apt-get update && \
      apt-get -y upgrade && \
      apt-get install -y build-essential && \
      apt-get install -y software-properties-common && \
      apt-get install -y byobu curl git htop man unzip vim wget && \
      apt-get install -y openjdk-7-jdk && \
      rm -rf /var/lib/apt/lists/*

# Set environment variables.
ENV HOME /root
ENV JAVA_HOME /usr/lib/jvm/java-7-openjdk-amd64

# Define working directory.
WORKDIR /work

# Define default command.
CMD ["bash"]
