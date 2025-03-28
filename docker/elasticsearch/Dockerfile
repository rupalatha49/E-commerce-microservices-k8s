# Set the build argument for Elasticsearch version
ARG ELASTIC_VERSION=8.5.0

# Use the official Elasticsearch image
FROM docker.elastic.co/elasticsearch/elasticsearch:${ELASTIC_VERSION}

# Set environment variables for single-node setup
ENV discovery.type=single-node \
    ES_JAVA_OPTS="-Xms512m -Xmx512m"

# Copy the custom Elasticsearch configuration
COPY config/elasticsearch.yml /usr/share/elasticsearch/config/elasticsearch.yml


USER root
RUN chown -R elasticsearch:elasticsearch /usr/share/elasticsearch/config/elasticsearch.yml
USER elasticsearch


# Expose Elasticsearch ports
EXPOSE 9200 9300

# Start Elasticsearch
CMD ["bin/elasticsearch"]
