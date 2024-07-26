# Docker Compose ELK Stack

This repository contains a Docker Compose configuration for deploying an ELK stack (Elasticsearch, Logstash, Kibana) along with Filebeat and a log collection application. This setup facilitates efficient log management, analysis, and visualization.

## Docker Compose Configuration

### Elasticsearch

- **Image**: `docker.elastic.co/elasticsearch/elasticsearch:7.15.0`
- **Port**: `9200`
- **Environment**: Configured for single-node mode.

### Kibana

- **Image**: `docker.elastic.co/kibana/kibana:7.15.0`
- **Port**: `5601`
- **Environment**: Configured to connect to Elasticsearch and disable HTTP authentication.

### Filebeat

- **Image**: Custom (defined in `.env`)
- **Command**: `filebeat -e -strict.perms=false`
- **Volume**: Collects logs from the mounted volume.

### App

- **Image**: `ur-img:ur-tag`
- **Port**: `5000`
- **Volume**: Provides logs to be collected by Filebeat.

## Setup and Usage

1. **Prepare the `.env` File**: Customize the `.env` file with your specific configuration settings.
2. **Run Docker Compose**: Execute the following command to start all services:

    ```bash
    docker-compose up
    ```

## Dependencies

- Docker
- Docker Compose
