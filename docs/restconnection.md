### class RestConnection
Connection make global connector by passed config

```js
import RestConnection from 'flespi-io-js/dist/rest'
```

The arguments are:
* `config` is a global config for all connections you have
    * `connectorName` is a name of global variable of connector(only for initialization Vue plugin)
    * `token` is a token for connections
    * `settings` config for http connections
        * `server` server for http connections
        * `port (optional)` port for http connections
        * `...axios settings` some axios settings


### getters and setters

```js
let connector = new RestConnection({
  token: 'FlespiToken xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx',
  settings: { server: 'https://server.io', port: 8080 }
})
```

* Token

```js
let token = connector.token
connector.token = 'FlespiToken XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX'
```

* settings

```js
let httpConfig = connector.settings
connector.settings = { server: 'http://server.io', port: 80 }
```

### Methods

* setRegion methods allows set flespi region for connection.
```js
  connector.setRegion(region)
  /* region structure */
  {
    "cdn": "https://ru-cdn.flespi.io",
    "default": false,
    "gw": "ru-gw.flespi.io",
    "mqtt": "ru-mqtt.flespi.io:8883",
    "mqtt-ws": "ru-mqtt.flespi.io:443",
    "region": "ru",
    "rest": "https://ru.flespi.io"
  }
```

### HTTP

Method for making http requests. It`s using axios as a dependency. So API of HTTP is the same as axios [HTTP API axios](https://github.com/axios/axios)
* `Connector#request(options)`: same options axios
* `Connector#request.get(url, [options])`,
* `Connector#request.delete(url, [options])`,
* `Connector#request.post(url, data, [options])`,
* `Connector#request.put(url,data, [options])`
    * `url` is the server URL that will be used for the request
    * `data` is the data to be sent as the request body
    * `options` are another options by axios API
* `Connector#request.external(oprions)`: to make requests to somewhere. Get full api of axios.

It has all sugar methods. Just replace `http` namespace to `request`.
