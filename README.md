# mqtt-bridge-example

Subscribe in Neuhausen to messages published in Essen:

```bash
mosquitto_sub -v -h localhost -p 1883 -t es/#
```

Publish a message from Essen to Neuhausen:

```bash
mosquitto_pub -h localhost -p 2883 -t nh/some/topic -m hello
```
