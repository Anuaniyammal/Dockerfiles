# Start with an Ubuntu base image
FROM ubuntu:latest

# Update package manager and install Java
RUN apt-get update && \
    apt-get install -y openjdk-11-jdk wget && \
    apt-get clean

# Set environment variable for JAVA_HOME
ENV JAVA_HOME /usr/lib/jvm/java-11-openjdk-amd64
RUN export JAVA_HOME

# Download and extract Tomcat
RUN wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.96/bin/apache-tomcat-9.0.96.tar.gz && \
    tar xzvf apache-tomcat-9.0.96.tar.gz && \
    mv apache-tomcat-9.0.96 /usr/local/tomcat && \
    rm apache-tomcat-9.0.96.tar.gz

# Set the working directory to Tomcat
WORKDIR /usr/local/tomcat

# Copy Amazon.war to the webapps directory
COPY Amazon.war webapps/

# Expose port 8080
EXPOSE 8080

# Set the entrypoint to start Tomcat
ENTRYPOINT ["sh", "bin/catalina.sh", "run"]

#checking how CMD works
CMD echo "Hello, Docker!"
