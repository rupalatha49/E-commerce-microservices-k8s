# Set the build argument for Logstash version
ARG ELASTIC_VERSION=8.6.2

# Use the official Logstash image
FROM docker.elastic.co/logstash/logstash:${ELASTIC_VERSION}

# Set environment variables
ENV LS_JAVA_OPTS="-Xms256m -Xmx256m"

# Copy the Logstash configuration
COPY config/logstash.yml /usr/share/logstash/config/logstash.yml

# Copy pipeline configuration
COPY pipeline/ /usr/share/logstash/pipeline/

# Set permissions for config files
RUN chmod 644 /usr/share/logstash/config/logstash.yml && \
    chmod -R 644 /usr/share/logstash/pipeline/


# Expose required ports
EXPOSE 5044 50000/tcp 50000/udp 9600

# Start Logstash
CMD ["logstash", "-f", "/usr/share/logstash/pipeline/"]
