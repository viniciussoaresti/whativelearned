# Mocha:

"Mocha is a feature-rich JavaScript test framework running on Node.js and in the browser, making asynchronous testing simple and fun. Mocha tests run serially, allowing for flexible and accurate reporting, while mapping uncaught exceptions to the correct test cases", [Mocha](https://mochajs.org/https://mochajs.org/).

## Installing:

Start a node project, for example:

```javascript
npm init -y
```

Install mocha:

```javascript
npm i --save-dev mocha
```

Modify package.json:

```javascript
{
  "name": "mochaTest",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "mocha"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "mocha": "^8.4.0"
  }
}

```

## Running:

Mocha will try to run tests on the src/test folder, for default. There, you can create test files, following the extension 'name'.spec.js. For example, on node.js (that provide us the assert class):

```javascript
// ./test/math.spec.js

const assert = require('assert');
const Math = require('../src/math.js');

describe('Math class', function(){
    it('should sum two numbers', function (){
        const math = new Math();
        assert.strictEqual(math.sum(5,5), 10);
    });
});

// ./src/math.js

class Math {
    sum(a, b) {
        return a + b;
    }
}

module.exports = Math;
```

Then run:

```javascript
npm run test
```

Then you should get:

```javascript
mochaTest@1.0.0 test C:\Users\sadfatboi\Documents\mochaTest     
> mocha



  Math class
    √ should sum two numbers


  1 passing (5ms)
```

## Tips:

To be able to handle asynchronous tests, mocha gives us the done argument on the 'it' function, and only evaluates the result when this argument is called. Modifying the last example:

```javascript
// ./test/math2.spec.js
describe('Math class', function () {
    it('should sum two numbers 2', function (done) {
        const math = new Math();
        math.sum(5, 5, value => {
            assert.strictEqual(value, 10);
            done();
        });
    });
});

// ./src/math2.js

class Math {
    sum(a, b, callback) {
        setTimeout(() => {
            callback(a+b);
        }, 100)
    }
}

module.exports = Math;
```

Just a detail, mocha's default timeout is 2000ms, which can be overwritten by:

```javascript
// ./test/math2.spec.js
describe('Math class', function () {
    it('should sum two numbers 2', function (done) {
        const math = new Math();
        this.timeout(3000); //3s for example
        math.sum(5, 5, value => {
            assert.strictEqual(value, 10);
            done();
        });
    });
});
```

We're also able to specify tests for functionalities that are yet to be developed:

```javascript
describe('Something', function () {
    it('Should do something unimplemented');
});

//It will return on the test as 'pending'
```

And only one test to be run:

```javascript
describe('Math class', function () {
    it('Should do something unimplemented 1');

    it.only('Should do something unimplemented 2', function(){
        assert.equal(1, 1);
    });
});
```

Or even skip tests:

```javascript
describe('Math class', function () {
    it.skip('Should do something unimplemented 1');

    it('Should do something unimplemented 2', function(){
        assert.equal(1, 1);
    });
});
```

Mocha also has 'hooks', like the beforeEach method, that for example, runs before every test. There's also the before, after and beforeEach, to mention some. Actually, I think Mocha's pretty similar to JUnit, in some aspects.

```javascript
describe('Math class', function () {
    beforeEach(function() {
        let value = 5;
    });

    it('Should do something unimplemented 1');

    it('Should do something unimplemented 2', function(){
        assert.equal(1, 1);
    });
});
```

## Chai

"Chai is a BDD / TDD assertion library for node and the browser that can be delightfully paired with any javascript testing framework", [Chai](https://www.chaijs.com/).

While the node's assert utilization allow us to do what we're supposed to do, it lacks the readability that Mocha gives us, for example. Chai is good at doing this.

### Installing:

Install chai:

```javascript
npm i --save-dev chai
```

### Running:

We just need to import the library and use it. Modifying one of the last examples:

```javascript
// ./test/math2.spec.js
const assert = require('assert');
const Math = require('../src/math2.js');
const expect = require('chai').expect;

describe('Math class', function () {
    it('should sum two numbers 2', function (done) {
        const math = new Math();
        math.sum(5, 5, value => {
            expect(value).to.equal(10);
            done();
        });
    });
});
```

Then just run it the same as you already would:

```javascript
npm run test
```

You should expect the same result.

### Tips:

You can use Chai to check if an object has a property:

```javascript
const expect = require('chai').expect;

describe('Something', function () {
    it('should do something', function () {
        const obj = {
            name: 'Vinícius Soares'
        };
        expect(obj.name).to.have.property('name');
    });
});
```

And if this property has a specific value:

```javascript
const expect = require('chai').expect;

describe('Something', function () {
    it('should do something', function () {
        const obj = {
            name: 'Vinícius Soares'
        };
        expect(obj.name)
        .to.have.property('name')
        .equal('Vinícius Soares');
    });
});
```

We can also compare objects (note the specific syntax to avoid errors like comparing the object's references):

```javascript
const expect = require('chai').expect;

describe('Something', function () {
    it('should do something', function () {
        const obj = {
            name: 'Vinícius Soares'
        };
        const obj2 = {
            name: 'Vinícius Soares'
        };
        expect(obj.name)
        .to.deep.equal(obj2);
    });
});
```

## Sinon

"Standalone test spies, stubs and mocks for JavaScript.
Works with any unit testing framework", [Sinon](https://sinonjs.org/).

Sinon is an important tool to test cases that involve functions being called inside functions, so you can assure it's all working as its supposed to.

```javascript
//Function
function once(fn) {
  var returnValue,
    called = false;
  return function () {
    if (!called) {
      called = true;
      returnValue = fn.apply(this, arguments);
    }
    return returnValue;
  };
}

//Sinon test paired with mocha
it("calls the original function", function () {
  var callback = sinon.fake();
  var proxy = once(callback);

  proxy();

  assert(callback.called);
});
```