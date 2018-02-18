# scopeChain

Offers a way to combine objects without copying values around. Its is usefull when using immutables or if you want to restrict object access.

> Caution this method uses a [Proxies](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy) and there for will only work in modern Browsers.


## Methods

### ScopeChain(`Object level`, `Object parent` [, ...`Object parent`])

  `level` 
  `parent`at least one Object that acts as parent 

#### Proxy Traps
All traps will use the level object first and then start ascending the parents. The `set` and `prototypeOf` traps will use the level object only.

## Examples

```javascript
var p1 = {
  "id" : "p1",
  "global" : "value"
};

var p2 = {
  "id" : "p2",
  "fu" : "bla"
};

var level = {
  id : "level",
  "fu" : "bar"
};

var sc1 = ScopeChain(p1, p2);
var sc2 = ScopeChain(level, sc2); //nested
var sc3 = ScopeChain(level, p1, p2); //the same as sc2

sc1.id //p1
sc1.fu //bla
sc1.global //value

sc3.fubar //bar
sc3.id //level



```
