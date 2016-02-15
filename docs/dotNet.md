---
layout: get-started
title: .Net docs | PubSubSQL
heading: .Net Client API
active: docs
excerpt: "Documentation for .Net language"
search_omit: true
---

### Connecting

Minimal connection requires port and host.


``` .net
using System;
using PubSubSQL;

PubSubSQL.Client client = new PubSubSQL.Client();

string address = "localhost:7777";
client.Connect(address);
```

### Running commands

All commands are ran using `execute` command which accepts query as parameter.

Function example:

``` .net
client.Execute("key Stocks Ticker");
```

### Subscribing to data

The following example sets up client connection and once the connection is ready it subscribes to changes in `Stocks` table
when `MarketCap` value is `MEGA CAP`.

``` .net
using System;
using PubSubSQL;

PubSubSQL.Client client = new PubSubSQL.Client();

string address = "localhost:7777";
client.Connect(address);

client.Execute("subscribe * from Stocks where MarketCap = 'MEGA CAP'");
string pubsubid = client.PubSubId;
Console.WriteLine("subscribed to Stocks pubsubid: {0}", pubsubid);

int timeout = 100;

while (client.WaitForPubSub(timeout))
{
    Console.WriteLine("*********************************");
    Console.WriteLine("Action:{0}", client.Action);
    while (client.NextRow())
    {
        int ordinal = 0;
        foreach (string column in client.Columns)
        {
          Console.Write("{0}:{1} ", column, client.GetValue(ordinal));
          ordinal++;
        }
        Console.WriteLine();
    }
}
```
