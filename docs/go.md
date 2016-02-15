---
layout: get-started
title: Go docs | PubSubSQL
heading: Go Client API
active: docs
excerpt: "Documentation for Go language"
search_omit: true
---

### Connecting

Minimal connection requires port and host.


``` go
import (
	"fmt"
	"github.com/pubsubsql/client"
)

client := new(pubsubsql.Client)

address := "localhost:7777"
err := client.Connect(address)
if checkError(err) {
	return
}
```

### Running commands

All commands are ran using `Execute` command which accepts query as parameter.

Function example:

``` go
client.Execute("tag Stocks MarketCap")
```

### Subscribing to data

The following example sets up client connection and once the connection is ready it subscribes to changes in `Stocks` table
when `MarketCap` value is `MEGA CAP`.

``` go
import (
	"fmt"
	"github.com/pubsubsql/client"
)

address := "localhost:7777"
err := client.Connect(address)
if checkError(err) {
	return
}

err = client.Execute("subscribe * from Stocks where MarketCap = 'MEGA CAP'")
checkError(err)
pubsubid := client.PubSubId()
fmt.Println("subscribed to Stocks pubsubid:", pubsubid)

for {
	err := client.WaitForPubSub(timeout)
	if checkError(err) {
		break
	}

	fmt.Println("*********************************")
	fmt.Println("Action:", client.Action())
	for {
		more, err := client.NextRow()
		if checkError(err) {
			break
		}
		for ordinal, column := range client.Columns() {
			fmt.Printf("%s:%s ", column, client.ValueByOrdinal(ordinal))
		}
		fmt.Println("")
		if !more {
			break
		}
	}
}
```
