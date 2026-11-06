# Devops

The `helm/app` chart deploys the frontend, backend, and PostgreSQL migration Job.
The migration Job gets `PDB_USER` from the backend ConfigMap and database
passwords from `app-db-credentials`; it does not depend on `doratou-secrets`.
The raw example Secret manifest uses placeholder values and is intentionally
not rendered by the chart.

Database passwords are mapped from `backend.databaseCredentials.existingSecret`
(default: `app-db-credentials`): `postgresql-password` becomes `PDB_PASSWORD` and
`redis-password` becomes `RDB_PASSWORD`. The secret name and source keys can be
overridden in values.

The migration Job runs as an Argo CD Sync hook after the chart ConfigMap and
before the backend Deployment. It runs on every sync and is deleted after a
successful run.
