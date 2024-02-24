# Home Assistant Docker Compose

Docker compose file for home assistant and my integrations. Integrations:
- InfluxDB
- Graphana
- Mosquitto (MQTT)
- Let's encrypt

- [Home Assistant Docker Compose](#home-assistant-docker-compose)
  - [Setup](#setup)
    - [Mosquitto](#mosquitto)
    - [InfluxDB](#influxdb)

## Setup

### Mosquitto

For authorization to work you will have to create users. **IN THEORY** it should work with:

Create a file `mosquitto/config/passwords` and enter `USER:PASSWORD_IN_CLEAR_TEXT`. Connect to mosquitto using
```shell
$ docker exec -it mosquitto sh
# in docker image
$ mkdir -p /etc/mosquitto
$ vi /etc/mosquitto/passwords
# add users with `user:password` to file, save and exit (:wq)
$ chmod 0700 /etc/mosquitto/passwords
$ mosquitto_passwd -U /etc/mosquitto/passwords
$ echo $?
# should be 0
```

### InfluxDB

Refer to: https://hub.docker.com/_/influxdb

```shell
$ docker exec influxdb influx setup \
      --username $USERNAME \
      --password $PASSWORD \
      --org $ORGANIZATION \
      --bucket $BUCKET \
      --force

$ docker exec influxdb influx auth list \
      --user homeassistant \
      --json | grep token | cut -d "\"" -f4
```
