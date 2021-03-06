# optimize-ready
Event listener for Google Optimize

Modified version of the [Page Hiding Snippet](https://developers.google.com/optimize/)

Allows developers to wait until Optimize has loaded before running certain bits of code.

This can be useful where Optimize is slow to load (say if loaded via GTM) and the site js depends on changes made in an Experiment (in our use case we needed to wait until making an API call, which was modfied depending on a global var set by Optimize)

## Usage

```javascript
// CommonJS
import optimizeReady from 'optimize-ready'
// AMD
const optimizeReady = require('optimize-ready');

optimizeReady({
  'GTM-XXXXXX': true
})

window.addEventListener('optimizeReady', function(e) {
  // code to be triggered
  // e.details.timeout returns true if event triggered by timeout
})
```

## Extra options

```javascript
optimizeReady({
  'GTM-XXXXXX': true
}, {
  timeout: 7000, //The max time (in milliseconds) the listener will wait before firing anyway. Set to null to only trigger if Optimize fires (only use if sure optimizeReady will fire before Optimize)
  dataLayer: 'dataLayer' //The name of property that references the dataLayer object.
})

```
