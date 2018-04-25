# hmacurl
`hmacurl` is a curl inspired command line utility that implements aws4 hmac signing for requests

<img width="10%" src="https://raw.github.com/golang-samples/gopher-vector/master/gopher.png"/>


### build
`git clone https://github.com/jburks725/hmacurl.git`

`go build`

## run
```
$ ./hmacurl -h
Usage:
  hmacurl [OPTIONS] url

Application Options:
  -X, --request=GET|POST                           the http method to use (GET)
  -d, --data='my string body'                      for POST requests, the data
                                                   to be uploaded as the body.
                                                   Used if -f is not provided.
  -f, --file=./file.txt                            for POST requests, the file
                                                   to be uploaded as the body.
                                                   Used if -d is not provided
  -H, --header='Content-Type: application/json'    Extra header(s) to include
                                                   in the request when sending
                                                   HTTP to a server. You may
                                                   specify any number of extra
                                                   headers.
      --curl-only                                  If specified, will only
                                                   print out a curl command -
                                                   not actually run a request
                                                   (false)
  -a, --access-key=                                The access Key to use in
                                                   HMAC signing. Can also be
                                                   specified as an environment
                                                   variable(export
                                                   HMACURL_ACCESS_KEY='fasdf')
  -s, --secret-key=                                The secret Key to use in
                                                   HMAC signing. Can also be
                                                   specified as an environment
                                                   variable(export
                                                   HMACURL_SECRET_KEY='fasdf')
  -c, --credential-scope=                          The credential scope (aka
                                                   Service Name) for the
                                                   request. Defaults to short
                                                   host name.
  -r, --region=                                    The region string to use in
                                                   the credential scope.
                                                   (default: us-east-1)
      --skip-host                                  Do not sign the Host header
                                                   (useful for non-standard
                                                   HMAC implementations) (false)
  -p, --proxy=                                     Proxy server to use if not
                                                   set via environment variable.
      --debug                                      Whether to output debug
                                                   information (false)

Help Options:
  -h, --help                                       Show this help message

Arguments:
  url
```

#### example
` ./hmacurl -XPOST -H'Content-Type: text/html' -H'foo:bar' -a accessKey -s secret -d'{}' http://example.com`
