# Build and Run the NATS-Replicator

## Running the server

The server will compile to an executable named `nats-replicator`. A [configuration](config.md) file is required to get any real behavior out of the server.

To specify the [configuration](config.md) file, use the `-c` flag:

```bash
% nats-replicator -c <config file>
```

You can use the `-D`, `-V` or `-DV` flags to turn on debug or verbose logging. The `-DV` option will turn on all logging, depending on the config file settings, these settings will override the ones in the config file.

<a name="build"></a>

## Building the Server

This project uses go modules and provides a make file. You should be able to simply:

```bash
% git clone https://github.com/nats-io/nats-replicator.git
% cd nats-replicator
% make
```

Use `make test` to run the tests, and `make install` to install. The nats and nats streaming servers are imported as go modules.

## Docker

You can build the docker image using:

```bash
% docker build . -t "nats-io/nats-replicator:0.5"
```

Then run it with:

```bash
% docker run -v <path to config>:/conf/replicator.conf "nats-io/nats-replicator:0.5" -c /conf/replicator.conf
```

Be sure to include your monitoring port, for example, if port 9090 is used for monitoring, you can run with:

```bash
% docker run -v <path to config>:/conf/replicator.conf -p 9090:9090 "nats-io/nats-replicator:0.5" -c /conf/replicator.conf
```
