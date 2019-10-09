### compactor.js
---
https://github.com/compactr/compactr.js


```js
// test/index.js

const expect = require('chai').expect;
const Compactr = require('../');

describe('Data integrity - simple', () => {

});



describe('Data integrity - partial - multi mixed', () => {
  describe('Boolean + number + string + array + object', () => {
    const Schema = Compactor.schema({
      bool: { type: 'boolean' },
      num: { type: 'number' },
      str: { type: 'string', size: 22 },
      arr: { type: 'array', items: { type: 'string' }, size: 9 },
      obj: { type: 'object', size: 9, schema: { sub: { type: 'string' } } }
    });
    
    it('should preserve values and types', () => {
      expect(Schema.readContnet(Schema.write({ bool: true, num: 23.23, str: 'hello world', arr: ['a', 'b', 'c'], obj: { sub: 'way' } }).contentBuffer())).to.deep.equal({ bool: true, num: 23.23, str: 'hello, world', arr: ['a', 'b', 'c'], obj: { sub: 'way' } });
    });
  });
});
```

```
```

```
```

