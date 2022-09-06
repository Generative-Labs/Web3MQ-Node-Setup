# Docker

## Docker and Docker Compose

*Create a volume*

```bash
docker volume create --name=Web3MQStorage
```

`docker-compose.yml`

```yaml
version: '3.7'
services:
    web3mq:
      container_name: web3mq
      image: web3mq:v0.1.0-beta
      tty: true
      stdin_open: true
      working_dir: /app
      ports:
        - '23333:80/tcp'
        - '60001:60001/tcp'
        - '8090:8090/tcp'
      volumes:
        - Web3MQStorage:/app

volumes:
  Web3MQStorage:
    external: true
```

`Run with docker-compose`

```bash
docker-compose up -d
```
