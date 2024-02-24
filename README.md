# Home Assistant Docker Compose

Docker compose file for home assistant and my integrations. Integrations:
- InfluxDB
- Graphana
- Mosquitto (MQTT)
- Let's encrypt


## Mosquitto Setup

Create a file `mosquitto/config/passwords` and enter `USER:PASSWORD_IN_CLEAR_TEXT`. Connect to mosquitto using
```shell
$ docker exec -it mosquitto sh
# in docker image
$ mkdir -p /etc/mosquitto
$ touch /etc/mosquitto/passwords
$ chmod 0700 /etc/mosquitto/passwords
$ mosquitto_passwd -U /etc/mosquitto/passwords

```

**NOTE** config folder and password file `/etc/mosquitto/passwords` have to be created first.
