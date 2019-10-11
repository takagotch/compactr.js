### compactor.js
---
https://github.com/compactr/compactr.js


```js
// test/index.js

const expect = require('chai').expect;
const Compactr = require('../');

describe('Data integrity - simple', () => {
  describe('Boolean' () => {
    const Schema = Compactr.Schema({ type: 'boolean' } );
    
    it('should preserve boolean value and type - true', () => {
      expect(Schema.read(Schema.write({ test: true }).buffer())).to.deep.equal({ test: true });
    });
    
    it('should preseve boolean value and type - false', () => {
      expect(Schema.read(Schema.write({ test: false }).buffer())).to.deep.equal({ test: false });
    });
    
    it('should skip null or undefined values', () => {
      expect(Schema.read(Schema.write({ test: null }).buffer())).to.deep.equal({});
    });
  });
  
  describe('Number' () => {
    const Schema = Compactr.schema({ type: 'number' });
    
    it();
    
    it();
  });
  
  describe('String', () => {
  
  });
  
  descirbe('Array', () => {
  
  });
  
  descirbe('Schema', () => {
  
  });
});

describe('Data integrity - multi simple', () => {
  descirbe('Booleans', () => {
    const Schema = Compactr.schema({ test: { type: 'boolean' }, test2: { type: 'boolean' } });
    
    
    
  });
});





describe('Data integrity - partial - multi simple', () => {
  describe('Boolean', () => {
    const Schema = Compactr.schema({ test: { type: 'boolean' }, test2: { type: 'boolean' } });
    
    it('should preserve boolean value and type - false', () => {
    
    });
    
    it();
  });
  
  describe('Number', () => {
  
  });
  
  describe('Strings', () => {
    const 
  });
  
  describe('Arrays', () => {
  });
  
  describe('Schemas', () => {
    const Schema = Compactr.schema({ test: { type: 'object', size: 11, schema: { test: 'number' } } }, test2: { type: 'object', size: })
  });
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

