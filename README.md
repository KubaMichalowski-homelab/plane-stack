# plane-stack

This repository contains the GitOps-driven configuration for my [Plane](https://github.com/makeplane/plane) deployment. It is designed to be managed and deployed via Portainer.

## Environment Setup
The stack relies on the following environment variables (defined in Portainer's Stack UI):

| Variable | Description | Example |
| :--- | :--- | :--- |
| `APP_DOMAIN` | Base domain for the app | `plane.domain.tld` |
| `WEB_URL` | URL for the frontend | `https://plane.domain.tld` |
| `CORS_ALLOWED_ORIGINS` | CORS policy origin | `https://plane.domain.tld` |
| `RABBITMQ_VHOST` | RABBITMQ VHOST | `plane` |
| `RABBITMQ_USER` | RABBITMQ user | `plane` |
| `RABBITMQ_PASSWORD` | RABBITMQ pasword | `(Secret)` |
| `POSTGRES_DB` | Postgres database name | `plane` |
| `POSTGRES_USER` | Postgres database user | `plane` |
| `POSTGRES_PASSWORD` | Postgres database password | `(Secret)` |
| `BUCKET_NAME` | Minio bucket for uploads | `uploads` |
| `MINIO_USER` | Minio user | `admin` |
| `MINIO_PASSWORD` | Minio password | `(Secret)` |
| `LIVE_SERVER_SECRET_KEY` | Server secret | `(Secret)` |
| `SECRET_KEY` | Django secret key | `(Secret)` |

## Persistent Storage
I use bind mounts for data persistence. Ensure these paths exist on the Docker host:
* `/opt/docker/plane/logs_*` - Logs for API, Worker, Beat, and Migrator
* `/opt/docker/plane/pgdata` - PostgreSQL database files
* `/opt/docker/plane/redisdata` - Valkey cache data
* `/opt/docker/plane/rabbitmq_data` - RabbitMQ message queues
* `/opt/docker/plane/uploads` - Minio object storage
* `/opt/docker/plane/proxy_config` - Proxy configurations
* `/opt/docker/plane/proxy_data` - Proxy data

---

[Back to Homelab Overview](https://github.com/KubaMichalowski-homelab)
