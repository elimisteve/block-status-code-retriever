# WebPipes Block: Status Code Retriever

[WebPipes](http://www.webpipes.org/) block written in
[Go](http://golang.org) which accepts a URL, visits that URL, then
returns the HTTP status code returned upon visiting it.


## Status Code Retriever

    curl -i -X POST -d '{"inputs":{"url":"http://google.com"}}' \
    -H "Content-Type: application/json" \
    http://status-code-retriever.herokuapp.com/

To run this example locally, clone the repo and start up the service:

```
git clone https://github.com/elimisteve/block-status-code-retriever
cd block-status-code-retriever
go run web.go
```

In another terminal, run this command:

    curl -i -X POST -d '{"inputs":{"url":"http://google.com"}}' \
    -H "Content-Type: application/json" \
    http://localhost:8080/

You should receive a response similar to the following:

```
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 35
Date: Wed, 04 Sep 2013 08:14:21 GMT

{"outputs": [{"status_code": 200}]}
```


## Block Definition

```javascript
{
  "name": "HTTP Status Code Retriever",
  "url": "http://status-code-retriever.herokuapp.com",
  "description": "Visits the given URL and returns the HTTP status code.",
  "inputs": {
      "name": "url",
      "type": "String",
      "description": "URL to be visited."
  },
  "outputs": {
      "name": "status_code",
      "type": "Number",
      "description": "HTTP status code returned by given URL."
  }
}
```
