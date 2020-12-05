# Use Java 8 slim JRE
FROM openjdk:8-jre-slim
MAINTAINER anees

# JMeter version
ARG JMETER_VERSION=5.2.1

# Install few utilities
RUN apt-get clean && \
    apt-get update && \
    apt-get -qy install \
                wget

# Install JMeter
RUN   mkdir /jmeter \
      && cd /jmeter/ \
      && wget https://archive.apache.org/dist/jmeter/binaries/apache-jmeter-$JMETER_VERSION.tgz \
      && tar -xzf apache-jmeter-$JMETER_VERSION.tgz \
      && rm apache-jmeter-$JMETER_VERSION.tgz

# ADD all the plugins
ADD jmeter_plugins/lib /jmeter/apache-jmeter-$JMETER_VERSION/lib

# ADD the jmx folder from host to image
ADD jmx jmx

#setting work directory
WORKDIR /jmx

# Set JMeter Home
ENV JMETER_HOME /jmeter/apache-jmeter-$JMETER_VERSION/

# Add JMeter to the Path
ENV PATH $JMETER_HOME/bin:$PATH

#running the test
ENTRYPOINT jmeter -n -t jmeter_testplan_jenkins.jmx -JuserCount=$userCount -Jrampup=$rampupTime -Jduration=$testDuration -Jkeywordss=$keywds -l results/test_results.csv
