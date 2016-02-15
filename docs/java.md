---
layout: get-started
title: Java docs | PubSubSQL
heading: Java Client API
active: docs
excerpt: "Documentation for Java language"
search_omit: true
---

### Connecting

Minimal connection requires port and host.


``` java
import pubsubsql.Client;

Client client = new Client();

String address = "localhost:7777";
client.connect(address);
```

### Running commands

All commands are ran using `execute` command which accepts query as parameter.

Function example:

``` java
client.execute("key Stocks Ticker");
```

### Subscribing to data

The following example sets up client connection and once the connection is ready it subscribes to changes in `Stocks` table
when `MarketCap` value is `MEGA CAP`.

``` java
import pubsubsql.Client;

Client client = new Client();

String address = "localhost:7777";
client.connect(address);

client.execute("subscribe * from Stocks where MarketCap = 'MEGA CAP'");
String pubsubid = client.getPubSubId();
System.out.println("subscribed to Stocks pubsubid: " + pubsubid);

int timeout = 100;
while (subscriber.waitForPubSub(timeout)) {
    System.out.println("*********************************");
	System.out.println("Action:" + subscriber.getAction());
	while (subscriber.nextRow()) {
	    System.out.println("New MEGA CAP stock:" + subscriber.getValue("Ticker"));
	    System.out.println("Price:" + subscriber.getValue("Price"));
	}
}
```
