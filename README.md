# Web3MQ-Node-Setup
Web3MQ-Node setup


## Install Binary

`Binaries on macOS, Linux`

```bash
curl -LO "https://github.com/Generative-Labs/Web3MQ-Node-Setup/releases/latest/download/Web3MQ-Node-$(uname -s | awk '{ print tolower($0) }')-x64.zip"

unzip Web3MQ-Node-*.zip
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
    "/ip4/52.77.28.6/tcp/60001/p2p/12D3KooWPxmYK6KzJ8dwuajbuJqB6yehZtrKd9x6PUZqBUkBKURc",
    "/ip4/18.138.163.201/tcp/60001/p2p/12D3KooWLgy8KE8gnX5a1HDMQKvVDWNf9tHgEbXRR5dYKsRjLKiJ",
    "/ip4/43.206.60.74/tcp/60001/p2p/12D3KooWLMnxXFoPzxTwRVjMC5griMdhud1hjLoUYK4cZta8oj9a",
    "/ip4/35.72.119.186/tcp/60001/p2p/12D3KooWBUKCX9K45HyJgMnmpqkdRkLHRB1BLktsNDvcD2H5EeEL",
    "/ip4/54.193.102.217/tcp/60001/p2p/12D3KooWKHnk31i1VbsXfGYukL24Bbu6FuihVBd2goAYGyp29iUN",
    "/ip4/54.215.25.183/tcp/60001/p2p/12D3KooWCKJZSyVio4P43QstzxA2L22Svz4icqGdgCtFgR8wdLd1"
  ]
  dbpath = "./store.db"
  keyfile = "./nodekey"
  p2p-port = 60001
  server-port = 23333
  usedb = true
  https-endpoint = ""
  testnet-devkey = ""
```

`Important`

> Write your domain in https-endpoint and
> Write your testnet devkey in testnet-devkey

*example*

```bash
https-endpoint = "https://yourdomain.com"
testnet-devkey = "testnet devkey"
```

`bootnodes array list`

- /ip4/52.77.28.6/tcp/60001/p2p/12D3KooWPxmYK6KzJ8dwuajbuJqB6yehZtrKd9x6PUZqBUkBKURc
- /ip4/18.138.163.201/tcp/60001/p2p/12D3KooWLgy8KE8gnX5a1HDMQKvVDWNf9tHgEbXRR5dYKsRjLKiJ
- /ip4/43.206.60.74/tcp/60001/p2p/12D3KooWLMnxXFoPzxTwRVjMC5griMdhud1hjLoUYK4cZta8oj9a
- /ip4/35.72.119.186/tcp/60001/p2p/12D3KooWBUKCX9K45HyJgMnmpqkdRkLHRB1BLktsNDvcD2H5EeEL
- /ip4/54.193.102.217/tcp/60001/p2p/12D3KooWKHnk31i1VbsXfGYukL24Bbu6FuihVBd2goAYGyp29iUN
- /ip4/54.215.25.183/tcp/60001/p2p/12D3KooWCKJZSyVio4P43QstzxA2L22Svz4icqGdgCtFgR8wdLd1

### Config Options description

- dbdriver // Support   sqlite(default) / mysql / postgres
- bootnodes default bootstrap nodes string array


`Run with config.toml`

```bash
./Web3MQ --config-file=config.toml
```

`Run in background`
```bash
nohup ./Web3MQ --config-file=config.toml &
```


