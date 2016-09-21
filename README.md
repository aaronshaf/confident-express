## Features

* Map each endpoint to a route controller
* Validate requests and responses
* Publish API documentation (by default at `/_docs`)

## Get started

### api.yaml

```yaml
swagger: '2.0'
info:
  title: Hello World
  version: 1.0.0
host: www.domain.com
schemes:
  - http
produces:
  - application/json
paths:
  /hello:
    get:
      operationId: greet
      responses:
        "200":
          description: Say hello to the world.
```

### greet.js

```javascript
module.exports = function (req, res) {
  res.json('Hello, world.');
};
```

### index.js

```javascript
const express = require('express');
const app = express();
const greet = require('./greet');

app.use(confident({
  definition: '/api.yml',
  controllers: { greet }
}));

app.listen(3000, function () {
  console.log('Example app listening on port 3000!');
});
```
