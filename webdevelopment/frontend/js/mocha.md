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

Mocha will try to run tests on the src/test folder, for default. There, you can create test files, following the extension 'name'.spec.js. For example:

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
// ./test/math.spec.js
describe('Math class', function () {
    it('should sum two numbers 2', function (done) {
        const math = new Math();
        math.sum(5, 5, value => {
            assert.strictEqual(value, 10);
            done();
        });
    });
});

// ./src/math.js

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
// ./test/math.spec.js
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