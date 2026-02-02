# Your Ultimate Developer Experience

A lightweight collection of Docker Compose configurations to quickly run common developer services locally:

- SQL Server 2022
- PostgreSQL
- MongoDB
- Redis
- RabbitMQ

## Prerequisites

- Docker Engine (desktop or engine)
- Docker Compose (v2+)

## Quick start

From the repository root:

Start all services:
```bash
docker compose up -d
```

Stop all services:
```bash
docker compose down
```

Start a single service (example):
```bash
docker compose -f directory/service.yaml up -d
```

Stop a single service:
```bash
docker compose -f directory/service.yaml down
```

## Redis

To connect to Redis using the CLI:

1. Install the Redis CLI (if not already installed):
```bash
brew install redis
```

2. Connect to your Redis server:
```bash
redis-cli -p 6379
```

The port is configured in `cache/.env`.

## RabbitMQ

To customize RabbitMQ configuration:

1. Copy the example definitions file:
```bash
cp .init/definitions.json.example .init/definitions.json
```
2. The project uses `rabbit_password_hashing_sha256`. To generate a password hash:
```bash
python .pwd/rabbit_pass_hash.py "your-password"
```
Use the produced hash in the `user` object inside `.init/definitions.json`.

Management UI is available once the container is running.

## Persistence

Service data is persisted using Docker volumes defined in the Compose files. Containers may be recreated without losing data.

## Resource limits

Compose files apply a conservative memory limit (256MB) to avoid over-consuming host resources. Adjust limits in the service YAML files if you need more memory.

## Troubleshooting & Contributing

- Check container logs: `docker compose logs -f <service>`
- Report issues or submit PRs via the repository issue tracker.