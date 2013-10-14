#connect-boobst
[![NPM version](https://badge.fury.io/js/connect-boobst.png)](http://badge.fury.io/js/connect-boobst)

connect-boobst is a Intersystems Caché session store backed by [boobst](https://github.com/agsh/boobst).

##Installation

via npm:

```
npm install connect-boobst
```

##Options
To start ```connect-boobst```, you have to pass function, returning an instance of boobst class, thus permitting the
usage of existing connections or server configurations.

Using an existing connection:
+ boobst Existing connection reference (instance of Boobst)

Or with a function:
+ getConnection

Other options:
+ global Name of a global where session will be stored
+ ns Namespace

##Example

``` Javascript
var connect = require('connect')
    , ConnectBoobst = require('connect-boobst')
    , BoobstSocket = require('boobst').BoobstSocket
    , sessionStore = new ConnectBoobst({
    	boobst: new BoobstSocket(
            host: 'localhost'
            , port: 6666
    	)
    })
    ;

connect.createServer(
    connect.bodyParser(),
    connect.cookieParser(),
    connect.session({
        secret: 'secret'
        , store: sessionStore
    });
);
```
