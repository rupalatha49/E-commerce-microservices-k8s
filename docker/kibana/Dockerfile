# Set the build argument for Kibana version
ARG ELASTIC_VERSION=8.6.2

# Use the official Kibana image
FROM docker.elastic.co/kibana/kibana:${ELASTIC_VERSION}

# Switch to root user to modify permissions
USER root

# Copy the Kibana configuration file
COPY config/kibana.yml /usr/share/kibana/config/kibana.yml

# Change ownership and permissions to allow Kibana to access the file
RUN chown kibana:kibana /usr/share/kibana/config/kibana.yml && \
    chmod 644 /usr/share/kibana/config/kibana.yml

# Switch back to Kibana user for security
USER kibana

# Expose Kibana web interface port
EXPOSE 5601

# Start Kibana
CMD ["kibana"]
