# node-caches
Node module that offers efficient caches that store key-value pairs.


## Available Classes
```javascript
/**
 * Fixed size cache storing key-value pairs such that total 
 * size of stored values will not exceed given limit. 
 * Uses the LFU algortihm (least frequently used) to evict entries if cache is full. 
 * Additionally an expire interval can be set (passive on put call) that repeatedly halfs 
 * the access counter of each entry.
 */
class FixedSizeLFUCache
```

```javascript
/**
 * Cache storing fixed amount of key-value pairs.
 * Uses the LFU algortihm (least frequently used) to evict entries if cache is full. 
 * Additionally an expire interval can be set (passive on put call) that repeatedly halfs 
 * the access counter of each entry.
 */
class FixedEntryLFUCache
```


## Example
```javascript
const {FixedSizeLFUCache} = require('node-caches');

let maxSize = 10.5; // MB
let cache = new FixedSizeLFUCache(maxSize);

cache.put("test", "Hello World");
cache.put("abc", Buffer.from("Some payload that should be store, e.g. contents of a file. Must not be of type string"));

cache.get("test"); // returns "Hello World" if entry still in cache
```
