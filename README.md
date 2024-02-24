# Home Assistant Docker Compose

Docker compose file for home assistant and my integrations. Integrations:
- InfluxDB
- Graphana
- Mosquitto (MQTT)
- Let's encrypt


## Mosquitto Setup

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
