# es-tabify

A function that converts ElasticSearch results into a table data structure. The returned table data structure is similar to that returned by [d3-dsv](https://github.com/d3/d3-dsv). Inspired by [Kibana's tabify implementation](https://github.com/elastic/kibana/blob/master/src/ui/public/agg_response/tabify/tabify.js). Works with `hits` style responses as well as nested aggregations.

See also this [Python port of this library](https://github.com/nickmaccarthy/python-tabify).

# Usage

`npm install es-tabify`

Here's an example use with the [official ElasticSearch JavaScript client](https://www.elastic.co/guide/en/elasticsearch/client/javascript-api/current/quick-start.html).

```js
var tabify = require('es-tabify');
var elasticsearch = require('elasticsearch');
var client = new elasticsearch.Client({
  host: 'localhost:9200',
  log: 'trace'
});

client.search({
  q: 'pants'
}).then(function (response) {
  var data = tabify(response);
}, function (error) {
  console.trace(error.message);
});
```

# Options

Pass in configuration options via object key/value.

```
var options = { debug: true };
var data = tabify(response, options);
```
* debug: (true | false:default) enable output debuging
