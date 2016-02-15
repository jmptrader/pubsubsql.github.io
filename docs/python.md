---
layout: get-started
title: Python docs | PubSubSQL
heading: Python Client API
active: docs
excerpt: "Documentation for Python language"
search_omit: true
---

### Connecting

Minimal connection requires port and host.


``` python
from pubsubsql import Client

client = Client()
address = "localhost:7777"

client.connect(address)
```

### Running commands

All commands are ran using `execute` command which accepts query as parameter.

Function example:

``` python
client.execute("tag Stocks MarketCap"
```

### Subscribing to data

The following example sets up client connection and once the connection is ready it subscribes to changes in `Stocks` table
when `MarketCap` value is `MEGA CAP`.

``` python
from pubsubsql import Client

client = Client()

address = "localhost:7777"
client.connect(address)

subscriber.execute("subscribe * from Stocks where MarketCap = 'MEGA CAP'")

pubsubId = client.getPubSubId()
print "subscribed to Stocks pubsubid:", pubsubId

timeout = 100
while client.waitForPubSub(timeout):
  print "*********************************"
  print "Action:{}".format(subscriber.getAction())
    while client.nextRow():
      print "New MEGA CAP stock:{}".format(client.getValue("Ticker"))
      print "Price:{}".format(client.getValue("Price"))

```
