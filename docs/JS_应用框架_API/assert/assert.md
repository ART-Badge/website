## Assert 模块介绍

Assert 模块提供给 JS 各种断言接口， Assert 模块设计参考自 IOTJS Assert 模块设计：[IOTJS Assert 模块说明](https://github.com/jerryscript-project/iotjs/blob/master/docs/api/IoT.js-API-Assert.md)

### errorTimes() 获取 Assert 模块错误触发统计次数。

* return : 返回错误触发统计次数。

当返回值大于0时外部掉调用 Assert 的测试接口有错误抛出

使用示例：

```js
if (assert.errorTimes() == 0) 
    console.log("Test pass");
else 
    console.log("Test fail");
```

### clearErrorTimes() 重置错误触发统计次数。

* 参数：无
* 返回值：无

重置错误触发统计次数。

使用示例：

```js
assert.clearErrorTimes();
```

### assert(value[, message，blocking])

* `value` {any}    ：测试值。
* `message` {any} ：在抛出错误时显示的消息.
* `blocking` {bool}    ：触发异常时是否阻塞，默认不阻塞

value 为 false 时用给定的操作及错误信息抛出错误(AssertionError). 

使用示例：

```js
var assert = require('assert');
assert.assert(1);
// OK
assert.assert(true);
// OK
assert.assert(false);
// 抛出错误

assert.assert(0);
// 抛出错误

assert.assert(false, "it's false");
// 抛出错误并给出错误提示信息 - "it's false"。
```


### equal(actual, expected[, message，blocking ])

* `actual` {any}       ：实际值。
* `expected` {any}    ：期待值。
* `message` {any}      ：提示信息
* `blocking` {bool}    ：触发异常时是否阻塞，默认不阻塞

当实际值不等于期待值时抛出异常，并给出提示信息。

使用示例：

```js
var assert = require('assert');

assert.equal(1, 1);
assert.equal(1, '1');
```

### notEqual(actual, expected[, message，blocking])

* `actual` {any}     ：实际值。
* `expected` {any}  ：期待值。
* `message` {any}    ：异常提示信息
* `blocking` {bool}    ：触发异常时是否阻塞，默认不阻塞

当实际值跟期待值同时抛出异常并给出提示信息。

使用示例

```js
var assert = require('assert');

assert.notEqual(1, 2);
```


### notStrictEqual(actual, expected[, message，blocking])

* `actual` {any}    ：实际值。
* `expected` {any} ：期待值。
* `message` {any}   ：异常提示信息
* `blocking` {bool}    ：触发异常时是否阻塞，默认不阻塞

当实际值跟期待值全等（===）时抛出异常信息并给出异常信息。

使用示例

```js
var assert = require('assert');

assert.notStrictEqual(1, 2);
// OK

assert.notStrictEqual(1, 1);
// AssertionError: 1 !== 1 全等抛出异常

assert.notStrictEqual(1, '1');
// OK
```


### strictEqual(actual, expected[, message，blocking ])

* `actual` {any}      ：实际值。
* `expected` {any}  ：期待值。
* `message` {any}    ：异常提示信息
* `blocking` {bool}    ：触发异常时是否阻塞，默认不阻塞

当实际值跟期待值不全等（!==）时抛出异常信息并给出异常信息。

使用示例

```js
var assert = require('assert');

assert.strictEqual(1, 1);
// OK

assert.strictEqual(1, 2);
// AssertionError: 1 === 2 不全等抛出异常

assert.strictEqual(1, '1');
// AssertionError: 1 === '1'
```


### throws(block[, expected, message])

* `block` {Function}       ： 抛出错误的函数。
* `expected` {Function}  ：预期的错误类型。
* `message` {any}            ：要显示的信息.

测试给定的函数是否抛出预期的异常，如果没有则抛出给定的异常信息

使用示例

```js
var assert = require('assert');

assert.throws(
  function() {
    assert.equal(1, 2);
  },
  assert.AssertionError
);
// assert.equal(1, 2); 将抛出异常，assert.throws正常

assert.throws(
  function() {
    assert.equal(1, 1);
  },
  assert.AssertionError
);
// assert.equal(1, 1); 没有抛出异常则 assert.throws抛出异常

assert.throws(
  function() {
    assert.equal(1, 2);
  },
  TypeError
);
// assert.equal(1, 2); 抛出的异常信息跟期待的 “TypeError”  类型不同，assert.throws抛出异常
```

### doesNotThrow(block[, message])

* `block` {Function} ： 抛出错误的函数。
* `message` {any}      ：异常提示信息

测试给定的函数是否不抛出任何异常。否则会抛出异常，并提示给定的提示信息.

使用示例

```js
var assert = require('assert');

assert.doesNotThrow(
  function() {
    assert.assert(1);
  }
);
// 给定的函数没有抛出异常

assert.doesNotThrow(
  function() {
    assert.assert(0);
  }, "Error occurd"
)
// 给定的函数将抛出异常, assert.doesNotThrow 将抛出异常, "Error occurd".
```
