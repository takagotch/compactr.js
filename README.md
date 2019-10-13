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
    
    it('should preserve number value and type', () => {
      expect(Schema.read(Schema.write({ test: 23.23 }).buffer())).to.deep.equal({ test: 23.23 });
    });
    
    it('should preserve number value and type for negative values', () => {
      expect(Schema.read(Schema.write({ test: -23.23 }).buffer())).to.deep.equal({ test: -23.23 });
    });
  });
  
  describe('String', () => {
    describe('Boolean', () => {
      const Schema = Compactr.schema({ test: { type: 'boolean' }});
      
      it('should preserve string value and type', () => {
        expect(Schema.read(Schema.write({ test: 'hello world' }).buffer())).to.deep.equal({ test: 'hello world' });
      });
    });
    
    describe('Array', () => {
      const Schema = Compactr.schema({ test: { type: 'array', items: { type: 'string' } } });
      
      it('should preserve array values and types', () => {
        expect(Schema.write({ test: ['a', 'b', 'c'] }).buffer()).to.deep.equal({ test: ['a', 'b', 'c'] });
      });
    });
    
    describe('Schema', () => {
      const Schema = Compactr.schema({ test: { type: 'object', schema: { test: { type: 'number' } } } });
    
      it('should preserve object values and types', () => {
        expect(Schema.read(Schema.write({ test: { test: 23.23 } }).buffer())).to.deep.equal({ test: { test: 23.23 } });
      });
    });
});

describe('Data integrity - multi simple', () => {
  descirbe('Booleans', () => {
    const Schema = Compactr.schema({ test: { type: 'boolean' }, test2: { type: 'boolean' } });
    
    it('should preserve boolean value and type - false', () => {
      expect(Schema.read(Schema.write({ test: false, test2: true }).buffer())).to.deep.equal({ test: false, test2: true });
    });
    
    it('should skip null or undefined values', () => {
      epxect(Schema.read({ test: null, test2: false }).buffer()).to.deep.equal({ test2: false });
    });
  });
  
  descirbe('Numbers', () => {
    const Schema = Compactr.schema({ test: { type: 'number' }, test2: { type: 'number' } });
    
    it('should preserve number value and type', () => {
      expect(Schema.read(Schema.write({ test: 23.23, test2: -97.7 }).buffer())).to.deep.equal({ test: 23.23, test2: -97.7 });
    });
  });
  
  describe('Strings', () => {
    const Schema = Compactr.schema({ test: { type: 'string' }, test2: { type: 'string' } });
    
    it('should preserve number and type', () => {
      expect(Schema.read(Schema.write({ test: 23.23, test2: -97.7 )).buffer()).to.deep.equal({ test: 23.23, test2: -97.7 });
    });
  });
  
  describe('Strings', () => {
    const Schema = Compactr.schema({ test: { type: 'string' }, test2: { type: 'string' } });
    
    it('should preserve string value and type', () => {
      expect(Schema.read(Schema.write({ test: 'hello world', test2: 'echo' }).buffer())).deep.equal({ test: 'hello world', test2: 'echo'})
    });
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

