## Features

* Map each endpoint to a route controller
* Validate requests and responses
* Publish API documentation

## Usage

### api.yaml

```yaml
swagger: '2.0'
info:
  version: 1.0.0
  title: Hello World
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

app.use(confident({
  definition: '/api.yml',
  documentationEndpoint: '/docs'
}));

app.listen(3000, function () {
  console.log('Example app listening on port 3000!');
});
```
