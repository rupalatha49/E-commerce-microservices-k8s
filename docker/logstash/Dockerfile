# Set the build argument for Logstash version
ARG ELASTIC_VERSION=8.6.2

# Use the official Logstash image
FROM docker.elastic.co/logstash/logstash:${ELASTIC_VERSION}

# Set environment variables
ENV LS_JAVA_OPTS="-Xms256m -Xmx256m"

# Switch to root user to set permissions
USER root

# Copy the Logstash configuration
COPY config/logstash.yml /usr/share/logstash/config/logstash.yml

# Copy pipeline configuration
COPY pipeline/ /usr/share/logstash/pipeline/

# Ensure Logstash user owns the files and set permissions
RUN chown -R logstash:logstash /usr/share/logstash/config/logstash.yml && \
    chown -R logstash:logstash /usr/share/logstash/pipeline/ && \
    chmod 644 /usr/share/logstash/config/logstash.yml && \
    chmod -R 755 /usr/share/logstash/pipeline/

# Switch back to Logstash user for security
USER logstash

# Expose required ports
EXPOSE 5044 50000/tcp 50000/udp 9600

# Start Logstash
CMD ["logstash", "-f", "/usr/share/logstash/pipeline/"]
