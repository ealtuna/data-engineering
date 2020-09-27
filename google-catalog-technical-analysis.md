Google Data Catalog (GDC) provides support to managed datasource metadata retrieval (no configuration needed) for Google Cloud Storage, Bigquery and Cloud Pub/Sub services. Users can also use GDC API to support metadata to any other datasource.

Some examples of connector supported by the community are MySQL, PostgreSQL, SQLServer, Redshift, Oracle, Teradata, Vertica and Greenplum. In a nutshell these connectors use the specific API of the RDBMS to extract the metadata about existing object and populates them in GDC using the provided public API. Using this architecture it's possible to create additional connectors for specific needs.

Conectors supported by the comunity are develop in Python. In order to use them you need execute and orchestrate using the method of choise. In the GCP there multiple possible options like:

 - Deploying in a VM and use cronjobs to execute
 - Use cloud functions in a serverless style using the schedule support on cloud functions.
 - Create a Cronjob object type in Kubernetes and schedule in GKE.
 - Using App Engine to create an endpoint and run with the cronjob support provided by App Engine.


References:

https://github.com/GoogleCloudPlatform/datacatalog-connectors-rdbms
