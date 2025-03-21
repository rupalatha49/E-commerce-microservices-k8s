# Set the build argument for Logstash version
ARG ELASTIC_VERSION=8.5.0

# Use the official Logstash image
FROM docker.elastic.co/logstash/logstash:${ELASTIC_VERSION}

# Set environment variables
ENV LS_JAVA_OPTS="-Xms256m -Xmx256m"

# Copy the Logstash configuration
COPY config/logstash.yml /usr/share/logstash/config/logstash.yml

# Expose required ports
EXPOSE 5044 50000/tcp 50000/udp 9600

# Start Logstash
CMD ["logstash"]
