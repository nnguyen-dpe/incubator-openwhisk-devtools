# How to setup OpenWhisk with Docker Compose

Follow these steps to get your environment ready:
1. Prerequisites
2. Quick Start
3. Install Kafka feed providers
4. Install wsk-cli
5. Install IBM cloud shell (optional)

### Prerequisites

The following are required to build and deploy OpenWhisk with Docker Compose:

- Mac OSX:
    - [Docker for Mac](https://www.docker.com/docker-mac) - only this currently works on Mac OSX
      + Install via homebrew: `brew cask install docker`
- Other Systems:
    - [Docker 1.13+](https://www.docker.com/products/docker)
    - [Docker Compose 1.6+](https://docs.docker.com/compose/install/)
- [Java 8](http://www.oracle.com/technetwork/java/javase/downloads/index.html)

These ports must be available:

- `80`, `443`, `9000`, `9001`, and `9090` for the API Gateway
- `6379` for Redis
- `2181` for Zookeeper
- `5984` for CouchDB
- `8085` for OpenWhisk's Invoker
- `8888` for OpenWhisk's Controller
- `9092` for Kafka
- `8001` for Kafka Topics UI

### Quick start

```bash
make quick-start
```

### Install Kafka feed providers

```bash
make create-provider-kafka
```

### Install wsk-cli

Follow instruction at https://openwhisk.apache.org/documentation.html#wsk-cli
> Note: make sure you always run the command with -i

Check if everything is set up properly
```sh
wsk -i property get
```

Check if package including /whisk.system/messaging and kafkaFeed
```sh
wsk -i package list /whisk.system
wsk -i package get --summary /whisk.system/messaging
```

### Install IBM cloud shell (optional)

IBM cloud shell provides better development experience than wsk-cli `https://github.com/ibm-functions/shell`
