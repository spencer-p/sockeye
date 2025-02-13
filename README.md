# sockeye

Websocket based CloudEvents viewer.

## Usage

Visit the root of the sockeye service in a web browser. Then `POST` CloudEvents
to the sockeye service and they will be displayed to the root page via a ws
connection.

Example curl:

```shell
curl -X POST -H "Content-Type: application/json" \
  -H "ce-specversion: 0.2" \
  -H "ce-source: curl-command" \
  -H "ce-type: curl.demo" \
  -H "ce-id: 123-abc" \
  -d '{"name":"Earl"}' \
  http://localhost:8080/
```

See also, the CloudEvents [Spec](https://github.com/cloudevents/spec) or
[golang SDK](https://github.com/cloudevents/sdk-go) to get started sending
CloudEvents formatted events.

## Running Locally

```shell
FILE_PATH=./cmd/sockeye/kodata go run cmd/sockeye/main.go
```

## Running on Kubernetes

### From Release 0.1.0

To install into the `default` namespace
```shell
kubectl apply -n default -f https://github.com/n3wscott/sockeye/releases/download/0.1.0/sockeye.yaml
```

### From Source

```shell
ko apply -f config/sockeye.yaml
```
