### Using MQTT Module
#### Install MQTT 

#### View the Module in Library


### Testing Pub-Sub in MQTT

#### Listen in topic : "mychannel"
```
mosquitto_pub -t "mychannel" -m "hola mundo!"
```

#### Send message to topic: "mychannel"
```
mosquitto_pub -t "mychannel" -m "hola mundo!"
```


#### Publish to cloud broker

Useful Flag Options and Examples
-r  Sets retain flag
-n  Sends Null message useful for clearing retain message.
-p – Set Port number Default is 1883
-u – Provide a username
-P – Provide a password
-i – Provide client name
-I – Provide a client id prefix- Used when testing client restrictions using prefix security.

We trying to send a message to shiftr.io
```
domain: brokeriot.cloud.shiftr.io <-> ip: 34.77.13.55
```
Example: 
```
mosquitto_pub -h 34.77.13.44 -m "Test message" -t iot2040/msg -u MyUser -P SecretPassword -d
```
