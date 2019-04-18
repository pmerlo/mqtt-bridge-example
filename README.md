# mqtt-bridge-example

Two-broker setup with bridge configuration.

## Instructions

Make sure `docker` and `docker-compose` are installed on your system.

Start the brokers:

```bash
docker-compose up --build
```

Broker `alpha` is mapped to local port `1883`.

Broker `bravo` is mapped to local port `2883`.

## From alpha to bravo

Subscribe to `some/topic` in bravo:

```bash
mosquitto_sub -v -h localhost -p 2883 -t some/topic
```

Publish to `some/topic` in alpha, prepended with `bravo/`:

```bash
mosquitto_pub -h localhost -p 1883 -t bravo/some/topic -m "hello"
```

The subscriber in bravo receives:

```
> some/topic hello
```

## From bravo to alpha

Subscribe to `another/topic` in alpha:

```bash
mosquitto_sub -v -h localhost -p 1883 -t another/topic
```

Publish to `another/topic` in bravo, prepended with `alpha/`:

```bash
mosquitto_pub -h localhost -p 2883 -t alpha/another/topic -m "hola"
```

The subscriber in alpha receives:

```
> another/topic hola
```
