1. You don't even have to run the server! You can use the one publicly available for testing at [public.pubsubsql.com](public.pubsubsql.com). If you do want to run the server, just do the following:

    ```shell
    $ go get github.com/pubsubsql/pubsubsql
    $ cd $GOPATH/src/github.com/pubsubsql/pubsubsql && go build && pubsubsql
    ```
    
3. Once server is running (or you use the public one) you can start coding your simple publisher:

    ```go
    package main

    import (
        "fmt"
        "math/rand"
        "time"

        "github.com/pubsubsql/client"
    )

    func CheckError(err error) {
        if err != nil {
            fmt.Println(err.Error())
        }
    }

    func main() {
        publisher := new(pubsubsql.Client)
        address := "public.pubsubsql.com:7777"
        publisher.Connect(address)

        publisher.Execute("key Stocks Ticker")
        publisher.Execute("tag Stocks MarketCap")
        publisher.Execute("insert into Stocks (Ticker, Price, MarketCap) values (GOOG, '1,2002d.22', 'MEGA CAP')")

        for {
            time.Sleep(300 * time.Millisecond)
            CheckError(publisher.Execute(fmt.Sprintf("update Stocks set Price='%f' where Ticker='GOOG'", 10000.0*rand.Float64())))
        }

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
        address := "public.pubsubsql.com:7777"
        subscriber.Connect(address)

        subscriber.Execute("subscribe * from Stocks where MarketCap = 'MEGA CAP'")
        pubsubid := subscriber.PubSubId()

        fmt.Println("subscribed to Stocks pubsubid:", pubsubid)

        // timeout after a minute of no data
        timeout := 60000

        var action string
        for {
            subscriber.WaitForPubSub(timeout)
            action = subscriber.Action()
            fmt.Println("Action:", action)

            for {
                more, err := subscriber.NextRow()
                if err != nil {
                    fmt.Println(err.Error())
                    break
                } else if more == false {
                    break
                }

                for ordinal, column := range subscriber.Columns() {
                    fmt.Printf("%s:%s ", column, subscriber.ValueByOrdinal(ordinal))
                }
                fmt.Println("")

            }
        }
    }
    ```
    
5. Profit!
