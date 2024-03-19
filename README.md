# Your Ultimate Developer Experience

The repository is my gift to all devs that are tired of installing the necessary services/frameworks when they buy a new computer.
Some of these components include:

- Sql Server (2022)
- PostgreSql
- MongoDb
- Redis Cache

This project uses [Docker](https://docs.docker.com/engine/) &amp; [Docker Compose](https://docs.docker.com/compose/) that allows you to bring any of the desired services to life quickly! 

You can choose to start or stop any of the service individually, or apply that to all of the services outlined in this project.

## Docker Compose

We'll be using the `docker compose` command throughout this project. To learn more about the base compose commands, refer to the [references page](https://docs.docker.com/compose/reference/).

## Individual Services

Locate the service that you like to work with, and use the file name in `docker compose` command.

To start a service, feel free to use the `-d` argument as detached.

```bash
docker compose -f directory/service.yaml up -d
```

When you're done with the service &amp; you'd like to stop it, run:

```bash
docker compose -f directory/service.yaml down`
```

## All Services
Feel free to use the `docker-compose.yaml` to start &amp; stop all of the services outlined in this project.

To do this, navigate to the root of the project's directory:

```bash
docker compose up -d
```

```bash
docker compose down
```

### Persistence

All of services outlined in this project will be using volumes as mounted data. The volumes are creatged and managed by docker. If your service gets interupted, and restarts, you would not lose your data.

### Memory Limits

Currently, I am using a **256mb** memory threshold limit on all container. I am doing this to avoid services such as database frameworks consuming as much memory as it can depriving the host from it's resources.