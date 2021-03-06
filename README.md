# NGINX Config AST
A parser and code generator for NGINX configuration files

## Usage:

```js
var parser = require('nginx-config-ast');

var config = `
    server {
        listen 80;

        server_name example.com;
        location / {
            root /etc/nginx/html;
            try_files $uri $uri/ $uri.html =404;
        }
    }
`;

// You can convert the configuration into an abstract tree (AST)
var ast = parser.generateAST(config);

// You can also convert the AST back to a configuration
var code = parser.generateConfig(ast);

```


# Methods

## `isConfigValid (config)`
Checks if the configuration is valid and returns a boolean.
### Arguments
* `config`: string - Code of a NGINX configuration file


## `generateAST (config, options)`
Generates and returns an abstract tree for specified configuration code.
### Arguments
* `config`: string - Code of a NGINX configuration file
* `options`: object
    * `noComments`: boolean - Strips all comments from the AST


## `generateConfig (ast)`
Generates and returns configuration code from an abstract tree.
### Arguments
* `ast`: object - Abstract tree for an NGINX configuration
    * See [src/parser.d.ts](./src/parser.d.ts) for typings