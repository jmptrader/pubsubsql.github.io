1. Once you're set up just get and run the server:

    ```shell
    $ go get github.com/pubsubsql/pubsubsql
    $ cd $GOPATH/src/github.com/pubsubsql/pubsubsql && go build && pubsubsql
    ```
    
3. Once server is running you can start coding your simple publisher:

    ```go
    package main

    import (
    	"fmt"
    	"github.com/pubsubsql/client"
    )

    func main() {
    	publisher := new(pubsubsql.Client)
	    address := "localhost:7777"
	    publisher.Connect(address)

    	publisher.Execute("key Stocks Ticker")
	    publisher.Execute("tag Stocks MarketCap")
	    publisher.Execute("insert into Stocks (Ticker, Price, MarketCap) values (GOOG, '1,200.22', 'MEGA CAP')")

	    fmt.Println("Msg published!")
    }
    ```
    
4. And here's the code for simple subscriber:

    ```go
    package main

    import (
	    "fmt"
	    "github.com/pubsubsql/client"
    )
    
    func main() {
	    subscriber := new(pubsubsql.Client)
	    address := "localhost:7777"
	    subscriber.Connect(address)

	    subscriber.Execute("subscribe * from Stocks where MarketCap = 'MEGA CAP'")
	    pubsubid := subscriber.PubSubId()

	    fmt.Println("subscribed to Stocks pubsubid:", pubsubid)

	    timeout := 100
	    subscriber.WaitForPubSub(timeout)

	    var action string
	    for {
		    action = subscriber.Action()
		    fmt.Println("Action:", action)

		    for {
			    more := subscriber.NextRow()

			    for ordinal, column := range subscriber.Columns() {
				    fmt.Printf("%s:%s ", column, subscriber.ValueByOrdinal(ordinal))
			    }
			    fmt.Println("")
			    if !more {
				    break
			    }
		    }
	    }
    }
    ```
    
5. Profit!
