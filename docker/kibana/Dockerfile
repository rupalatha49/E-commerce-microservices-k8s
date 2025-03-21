# Set the build argument for Kibana version
ARG ELASTIC_VERSION=8.5.0

# Use the official Kibana image
FROM docker.elastic.co/kibana/kibana:${ELASTIC_VERSION}

# Copy the Kibana configuration file
COPY config/kibana.yml /usr/share/kibana/config/kibana.yml

# Expose Kibana web interface port
EXPOSE 5601

# Start Kibana
CMD ["kibana"]
