# System Services

Some generic services are useful for any configuration.
They handle things like data storage, and communication between services.

These services will be used in all other example configurations.

::: tip
TODO: add GUI service(s)
:::

```yaml
version: '3'

services:
    eventbus:
        image: rabbitmq:latest

    influx:
        image: hypriot/rpi-influxdb:latest
        volumes:
            - "./influxdb:/var/lib/influxdb"

    history:
        image: brewblox/brewblox-history:rpi-latest
        depends_on:
            - influx
            - eventbus
        labels:
            - "traefik.port=5000"
            - "traefik.frontend.rule=PathPrefix: /history"

    traefik:
        image: traefik
        command: -c /dev/null --api --docker --docker.domain=docker.localhost
        ports:
            - "80:80"
            - "8080:8080"
        volumes:
            - /var/run/docker.sock:/var/run/docker.sock
```

## Service: eventbus

```yaml
eventbus:
    image: rabbitmq:latest
```

The [RabbitMQ](https://www.rabbitmq.com/) `eventbus` service allows other services to exchange messages. 
It can only be seen by services in this project.

## Service: influx

```yaml
influx:
    image: hypriot/rpi-influxdb:latest
    volumes:
        - "./influxdb:/var/lib/influxdb"
```

`influx` is an [InfluxDB](https://www.influxdata.com/) database.

It stores all the data generated by devices in the project.
To use it in BrewBlox projects, it should be combined with a `brewblox-history` service.

It uses a single volume: the `influxdb/` directory. This makes sure that the data still exists after the service exits.

## Service: history

```yaml
history:
    image: brewblox/brewblox-history:rpi-latest
    depends_on:
        - influx
        - eventbus
    labels:
        - "traefik.port=5000"
        - "traefik.frontend.rule=PathPrefix: /history"
```

`history` uses the `influx` service to store and read data. </br>
When the GUI wants to display a history graph, it gets the data from the `history` service.

The `traefik.frontend.rule=PathPrefix: /history` label indicates that all HTTP requests starting with `/history` are sent here.

If your Raspberry is called `raspberrypi` (the default name), you can try this out by going to `http://raspberrypi/history/api/doc` in your browser.

## Service: traefik

```yaml
traefik:
    image: traefik
    command: -c /dev/null --api --docker --docker.domain=docker.localhost
    ports:
        - "80:80"
        - "8080:8080"
    volumes:
        - /var/run/docker.sock:/var/run/docker.sock
```

This service allows outside clients (your browser) to talk to all services using the same address.
The `traefik.frontend.rule=PathPrefix: /service-name` labels are interpreted here.