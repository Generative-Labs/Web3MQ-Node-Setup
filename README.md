# Web3MQ-Node-Setup
Web3MQ-Node setup


## Install Binary

`Binaries on macOS, Linux`

```bash
v=v0.1.0-beta.1; curl -LO "curl -LO "https://github.com/Generative-Labs/Web3MQ-Node-Setup/releases/download/$v/Web3MQ-Node-$(uname -s | awk '{ print tolower($0) }')-x64-$v.zip"

v=v0.1.0-beta.1; unzip Web3MQ-Node-*-$v.zip
```

### QuickStart

`init`

```bash
./Web3MQ --init
```

`This command include several actions`

- Generate nodekey `Important it's node unique identification`
- Generate config.toml `You can change config file settings`
- Init DataBase `Default is SQLite`
    - We recommend running with a PostgreSQL database, you can change settings in config.toml

`Run with config.toml`

```bash
./Web3MQ --config-file=config.toml
```


## Docker and Docker Compose


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

`Run cmd docker-compose up -d`

```bash
docker-compose up -d
```
