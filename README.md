## 如何实现符合 Promise/A+ 规范的promise
### 什么是promise
```
promise本意是承诺的意思，promise是异步编程的一种解决方案。promise对象简单的说是一个保存着某个未来会结束的事件（通常是一个异步操作）的结果。比如：读取文件，网络请求等。
```
### promise 的优缺点：
```
1.promise对象内部维护了三种状态，pending,fulfilled,rejected.状态一但改变就不会再变。
2.promise无法取消，一旦建立它就会立即执行，如果不设置回调函数，Promise内部会抛出错误；当处于pending状态时，无法得知目前进展到哪个阶段。
```
### promise 解决了什么问题
- 1.解决多个异步操作并行的问题
- 2.解决回调地狱的问题
### 首先了解ES6中promise的使用方法
- 1.promise 对象是一个构造函数，用new 生成promise实例。接收一个函数作为参数，函数有两个参数，分别是resolve和reject
```javascript
var promise = new Promise( function( resolve, reject) {
       //some code
      if(//异步操作成功){
        resolve(value);
         }else{
         reject(error);
         }
});
```
- 2.Promise.prototype.then()实现链式调用
- 3.Promise.all()   接收一个promise数组当所有的promise都成功是返回一个成功的promise;如果数组中有个promise失败，则返回一个失败的promise。一般用于请求多个相关的资源或者是相关联的回调函数。
- 4.Promise.rece() 接收一个promise数组，数组中有一个先达到成功状态就返回一个成功的promise;有一个先达到失败状态，就返回失败的promise.
- 5.Promise.resolve()  返回一个成功的promise对象
- 6.promise.reject()   返回一个拒绝的promise对象

### 那么如何自己实现一个基于 Promsie/A+规范的promise对象呢
- 参考资料
- https://promisesaplus.com/
