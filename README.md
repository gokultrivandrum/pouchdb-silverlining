pouchdb-silverlining
=====

[![Build Status](https://travis-ci.org/ibm-watson-data-lab/pouchdb-silverlining.svg)](https://travis-ci.org/ibm-watson-data-lab/pouchdb-silverlining)

The *pouchdb-silverlining* project is a [PouchDB](https://pouchdb.com) plugin that allows SQL queries to be performed against PouchDB databases. This mirrors the functionality found in the [silverlining](https://www.npmjs.com/package/silverlining) library.

## Installation

To use this plugin, include it after `pouchdb.js` in your HTML page:

```html
<script src="pouchdb.js"></script>
<script src="pouchdb.silverlining.js"></script>
```

Or to use it in Node.js, just npm install it:

```
npm install pouchdb-myplugin
```

And then attach it to the `PouchDB` object:

```js
var PouchDB = require('pouchdb');
PouchDB.plugin(require('pouchdb-silverlining'));
```

## Usage

Connect to your database as normal:

```
var db = new PouchDB('mydb');
```

and then query with SQL:

```
db.sql("SELECT name, cost FROM animals WHERE collection = 'cats' ORDER BY name DESC LIMIT 50").then(console.log);
```



## Building

    npm install
    npm run build

Your plugin is now located at `dist/pouchdb.silverlining.js` and `dist/pouchdb.silverlining.min.js` and is ready for distribution.


## Testing

### In Node

This will run the tests in Node using LevelDB:

    npm test
    
You can also check for 100% code coverage using:

    npm run coverage

If you don't like the coverage results, change the values from 100 to something else in `package.json`, or add `/*istanbul ignore */` comments.


If you have mocha installed globally you can run single test with:
```
TEST_DB=local mocha --reporter spec --grep search_phrase
```

The `TEST_DB` environment variable specifies the database that PouchDB should use (see `package.json`).

### In the browser

Run `npm run dev` and then point your favorite browser to [http://127.0.0.1:8001/test/index.html](http://127.0.0.1:8001/test/index.html).

The query param `?grep=mysearch` will search for tests matching `mysearch`.

### Automated browser tests

You can run e.g.

    CLIENT=selenium:firefox npm test
    CLIENT=selenium:phantomjs npm test

This will run the tests automatically and the process will exit with a 0 or a 1 when it's done. Firefox uses IndexedDB, and PhantomJS uses WebSQL.



