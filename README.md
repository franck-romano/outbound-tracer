# Hinout
Trace any inbounding and outbounding http requests from your Node.js application.

### Motivation

This module aims to ease logging of outbounding and inbounding http requests.

### How it works ?

Each http client library like [Axios](https://github.com/axios/axios) or [Request](https://github.com/request/request) are using http and https Node.js internal modules.
So basically, `Hinout` adds listeners to those modules and emits an event once the request is gone or when the application receives a response.
As soon as the event is fired, a formatter formats the event and passes the result to `console.log` which is used by default as logging function.

### Usage

Simply import the module in any file of your application:

```js
import Hinout from 'hinout'
```

Then start collecting using :

```js
Hinout.collect()
```

Each http request will be logged using `console.log` by default.

Here's an example of an `outbound` and `inbound` formatted log:
	
	[1577367889] OUT - GET http://localhost:8080/path
	[1577367890] IN - HTTP 1.1 200 OK - Elapsed Time 0s 200ms


### API
**collect()** 

Listen and log every http requests using `console.log` as default logging function

Returns an intance of `Hinout`

**setLoggingFunction(loggingFunction)**


Override default logging function (`console.log`)

```js
Hinout.setLoggingFunction(yourLoggger.info)

// yourLogger.info() will now be used as logging function
```
Returns an intance of `Hinout`

### What is missing ?
This project is in its early stage, so feel free to contribute ! :)

- [ ] Blacklist some target host
- [ ] Logging payload and response of an HTTP request
- [X] Add timestamp in logs
- [X] Add elapsed time of request in logs
- [X] Support for HTTPS requests
- [X] Support for Node.js version < 8.X.X
- [X] Integration with existing logging libraries (for example [pino](https://github.com/pinojs/pino) or [winston](https://github.com/winstonjs/winston))
