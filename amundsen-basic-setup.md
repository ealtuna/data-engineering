## External dependencies

 - Neo4j: external database to store metadata in the relationship graph.
 - ElasticSearch: search over metadata objects.
 - Apache Airflow: schedule the execution of jobs to update the metadata from sources.
 
## Installation options

 - Docker images: using a container orchestration method of choise.
 - Kubernetes: using the official chart (https://github.com/amundsen-io/amundsen/tree/master/amundsen-kube-helm)
 
## Installation with Docker

The system is organized in three high level components:

 - Metadata service: Backend core pieze of the system, used to manage the metadata using Neo4j as datasource.
 - Search service: Backend service to execute search queries over ElasticSearch.
 - Frontend: NodeJS application.
 
Images use different versions of Ubuntu, based in the Slim version.

## Metadata service

Image: amundsendev/amundsen-metadata
Current version: 2.0.0

Environment:

 - PROXY_HOST=bolt://neo4j_host
 
Command: gunicorn -w 2 --bind :PORT metadata_service.metadata_wsgi

## Search service

Image: amundsendev/amundsen-search
Current version: 2.1.3

Environment:

 - PROXY_ENDPOINT=elasticsearch_host
 
Command: gunicorn -w 2 --bind :PORT search_service.search_wsgi

## Frontend

Image: amundsendev/amundsen-frontend
Current version: 2.1.1

Environment:

 - SEARCHSERVICE_BASE=http://search-service-host:PORT
 - METADATASERVICE_BASE=http://metadata-service-host:PORT
 
Command: gunicorn -w 2 --bind :PORT amundsen_application.wsgi

## Next steps

Configura authentication (https://github.com/amundsen-io/amundsen/blob/master/docs/authentication/oidc.md)
Use Apache Airflow tasks to update metadata (https://github.com/amundsen-io/amundsen/blob/master/docs/tutorials/index-postgres.md)
