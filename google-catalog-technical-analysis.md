Google Data Catalog (GDC) provides support to managed datasource metadata retrieval (no configuration needed) for Google Cloud Storage, Bigquery and Cloud Pub/Sub services. Users can also use GDC API to support metadata to any other datasource.

Some examples of connector supported by the community are MySQL, PostgreSQL, SQLServer, Redshift, Oracle, Teradata, Vertica, Greenplum, Looker, Tableau, Hive and Apache Atlas. In a nutshell these connectors use the specific API of the source system to extract the metadata about existing objects and populates them in GDC using the provided public API. Using this architecture it's possible to create additional connectors for specific needs. Extracted objects are classified as table, dataset, data stream, fileset and view.

Connectors supported by the community are develop in Python. In order to use them you need execute and orchestrate using the method of choice. In the GCP there multiple possible options like:

Deploying in a VM and use cronjobs to execute

Use cloud functions in a serverless style using the schedule support on cloud functions.

Create a Cronjob object type in Kubernetes and schedule in GKE.

Using App Engine to create an endpoint and run with the cronjob support provided by App Engine.

For standar connectors the only support provided is the extraction of tables, fields and data types. The Catalog promotes the concept of tag templates. Using tag templates you can define families of tags to apply to tables and fields. By default GDC do not fill any tag related information, but you can create your own in custom integrations.

For the natively supported objects GDC provides automatic security integration. For example, if you have access to see data in a Bigquery table then you are able to see sample data in GDC, if you can see metadata of a table in Bigquery then you can see the metadata in GDC, if you have no access in Bigquery the table will not show. In the connectors supported by the community there is no security support, all objects are visible to all users, but you can create personalizations to address those issues.

References:

https://www.youtube.com/watch?v=Qq76r-z_50c
https://github.com/GoogleCloudPlatform/datacatalog-connectors
https://github.com/GoogleCloudPlatform/datacatalog-connectors-rdbms
