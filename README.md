# dot-json
[![Build Status](https://travis-ci.org/crobays/dot-json.svg?branch=master)](https://travis-ci.org/crobays/dot-json)
---

Easily edit a json file from the CLI or NodeJS.

### Install global
```bash
npm install -g dot-json
```
or local
```bash
npm install --save dot-json
```
### Use from the CLI
```bash
dot-json myfile.json user.name "John Doe"
dot-json myfile.json user.email "john@example.com"
```
myfile.json now looks like
```json
{
    "user": {
        "name": "John Doe",
        "email": "john@example.com"
    }
}
```

```bash
dot-json myfile.json user.name
John Doe
```
```
Usage:
  dot-json <file> <key-path>             Get a value from a json file by key-path
  dot-json <file> <key-path> <value>     Assign a value at a key-path
  dot-json <file> <key-path> --delete    Delete a key by key-path

Options:
  -d --delete     Delete the key-path
  -h --help       Show this message with options
  -v --version    Print the version number
```

### Quick tip for editing package.json
Add to .bash_profile:
```bash
alias package="dot-json package.json"
```
Use it like this:
```bash
package name "my-package"
```

### Use it in NodeJS
#### Initialization
```javascript
var DotJson = require('dot_json');
var myfile = new DotJson('myfile.json');
```

#### Writing
asynchronous
```javascript
myfile.set('user.name', 'John Doe').set('user.email', 'john@example.com').save(function(){
  console.log('saved');
});
```

synchronous
```javascript
myfile.set('user.name', 'John Doe').set('user.email', 'john@example.com').save();
```

myfile.json now looks like
```json
{
    "user": {
        "name": "John Doe",
        "email": "john@example.com"
    }
}
```

#### Reading
asynchronous
```javascript
myfile.get('user.name', function(value){
  // value = 'John Doe'
  console.log(value);
});
```

synchronous
```javascript
var value = myfile.get('user.name');
// value = 'John Doe'
console.log(value);
```

#### Deleting
asynchronous
```javascript
myfile.delete('user.name').save(function(){
  console.log('saved');
});
```

synchronous
```javascript
myfile.delete('user.name').save();
```

myfile.json now looks like
```json
{
    "user": {
        "email": "john@example.com"
    }
}
```

[npmjs.org/package/dot-json](https://npmjs.org/package/dot-json)
