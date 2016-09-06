# Express Gen For Mocha/Chai

- express --hbs --git
- npm install --save-dev chai
- npm install --save-dev supertest


### add-spec.js test file
```javascript
const chai = require('chai');
const supertest = require('supertest');

const app = require('../app.js');

const should = chai.should();
const expect = chai.expect;
const assert = chai.assert;

const api = supertest(app);


describe('should succeed', function(){
    it('in adding two numbers together', function(done){
      api.post('/api/add')
        .send({
          num1: 5,
          num2: 2
        })
        .expect(200)
        .end((err, res) => {
          if(err) return done(err);

          res.body.result.should.be.equal(7);

          done();
        });
    });
    
