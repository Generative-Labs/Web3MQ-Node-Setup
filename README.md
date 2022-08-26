# Web3MQ-Node-Setup
Web3MQ-Node setup


## Install Binary

`Binaries on macOS, Linux`

```bash
v=v0.1.0-beta.2; curl -LO "curl -LO "https://github.com/Generative-Labs/Web3MQ-Node-Setup/releases/download/$v/Web3MQ-Node-$(uname -s | awk '{ print tolower($0) }')-x64-$v.zip"

v=v0.1.0-beta.2; unzip Web3MQ-Node-*-$v.zip
```

### QuickStart

`init`

```bash
# server port default is 80, you can change when init
./Web3MQ --init --server-port=23333
```

`This command include several actions`

- Generate nodekey `Important it's node unique identification`
- Generate config.toml `You can change config file settings`
- Init DataBase `Default is SQLite`
    - We recommend running with a PostgreSQL database, you can change settings in config.toml

`config.toml example`

```toml
[web3db]
  dbdriver = "sqlite"
  dbhost = "127.0.0.1"
  dbname = "Web3MQ"
  dbpassword = ""
  dbport = 0
  dbuser = ""

[web3mq]
  bootnodes = [
    "/ip4/35.79.142.79/tcp/60001/p2p/12D3KooWAxLmzfTLj2oS7X9DV1fC35E5qSMXiJP5xcM2NpvHMTwZ",
    "/ip4/18.140.146.199/tcp/60001/p2p/12D3KooWRsdkMk4ick1NnGQmHB4FAu7EVHQ1yrvG3s1zVdTyVVXP",
    "/ip4/52.36.178.129/tcp/60001/p2p/12D3KooWAM36rSzAmJjDV8XoMa59wNzvbdaKjM2NK8acKTe5TSFk"
  ]
  dbpath = "./store.db"
  keyfile = "./nodekey"
  p2p-port = 60001
  server-port = 23333
  usedb = true
```

`bootnodes array list`

- /ip4/35.79.142.79/tcp/60001/p2p/12D3KooWAxLmzfTLj2oS7X9DV1fC35E5qSMXiJP5xcM2NpvHMTwZ
- /ip4/18.140.146.199/tcp/60001/p2p/12D3KooWRsdkMk4ick1NnGQmHB4FAu7EVHQ1yrvG3s1zVdTyVVXP
- /ip4/52.36.178.129/tcp/60001/p2p/12D3KooWAM36rSzAmJjDV8XoMa59wNzvbdaKjM2NK8acKTe5TSFk


### Config Options description

- dbdriver // Support   sqlite(default) / mysql / postgres
- bootnodes default bootstrap nodes string array


`Run with config.toml`

```bash
./Web3MQ --config-file=config.toml
```


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
