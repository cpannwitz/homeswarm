# homeswarm
Docker Swarm stack as evolution to [cpannwitz/homeserver](https://github.com/cpannwitz/homeserver).

## Pre-configuration
Create/fill out different configuration files:
- `configs/example-ddclient.conf`

Populate configs to [Docker Configs](https://docs.docker.com/engine/swarm/configs/):
```
docker config create CONFIGNAME ./configs/CONFIGFILE
```

Following configs are requrired currently:
- `ddclientconfig` - used by `ddclient-stack.yml`, must follow ddclient [config template](https://github.com/ddclient/ddclient/blob/develop/ddclient.conf.in).

## Installation

Install different stacks:
```
env $(cat .env | grep ^[A-Z] | xargs) docker stack deploy -c STACK_FILE.yml STACK_NAME
```

Following stacks are available (in useful deploy order):
- `ddclient-stack` (enabling dynDNS for domains, useful for homeservers behind router)
- `traefik-stack` (enabling traefik reverse proxy, mandatory)