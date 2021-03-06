# Node.js vs. Spray vs. Erlang vs. Http-kit vs. Warp vs. Tornado

Comparison of raw HTTP hit performance of:

- [Node.js](http://nodejs.org)
- [Spray (Scala)](http://spray.io)
- [Erlang HTTP server](http://erlang.org/doc/apps/inets/http_server.html)
- [Http-kit (Clojure)](http://http-kit.org/index.html)
- [Warp (Haskell)](http://hackage.haskell.org/package/warp)
- [Tornado](http://www.tornadoweb.org/en/stable/)

## Results

See `*-results.txt` for `wrk` benchmark results.

| Environment | Req/s (concurrency 1) | Req/s (concurrency 10) | Req/s (concurrency 50) | Req/s (concurrency 100) |
|-------------|----------------------:|-----------------------:|-----------------------:|------------------------:|
| Node.js     |               8590.95 |               19619.37 |               19217.57 |                19606.67 |
| Spray       |               7595.75 |               18592.71 |               29571.34 |                31541.73 |
| Erlang      |               6750.29 |               15574.33 |               13455.14 |                13931.52 |
| Http-kit    |              10145.90 |               34416.03 |               36520.01 |                34391.64 |
| Warp        |              12640.29 |               27749.54 |               26365.52 |                23916.69 |
| Tornado     |               2356.82 |                4590.33 |                4422.08 |                 4155.61 |


## I don't believe you!

You can checkout the repo and do benchmarking yourself.

Starting Node.js app:

    $ cd node
    $ node main.js
    Open new terminal window.
    $ ../do-benchmark.sh http://127.0.0.1:8080/

Starting Spray (Scala) app:

    $ cd spray
    $ sbt run
    Open new terminal window.
    $ ../do-benchmark.sh http://127.0.0.1:8080/

Starting Erlang app:

    $ cd erlang
    $ erl
    $ c(erlanghttp).
    $ erlanghttp:start().
    Open new terminal window.
    $ ../do-benchmark.sh http://127.0.0.1:8080/

Starting Http-kit app:

    $ cd httpkit
    $ lein run
    Open new terminal window.
    $ ../do-benchmark.sh http://127.0.0.1:8080/

Starting Warp (Haskell) app:

    $ cd warp
    $ ./warped
    Open new terminal window.
    $ ../do-benchmark.sh http://127.0.0.1:8080/

    # To compile, run:
    $ cd warp
    $ ghc -O3 warped.hs

## Kudos to

- [@olegsmith](https://github.com/olegsmith) for fixing Node.js to use clustering and Erlang benchmark
- [@ollie](https://github.com/ollie) for Warp code
