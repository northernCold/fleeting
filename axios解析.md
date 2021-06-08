# axios解析

## axios拦截器原理

axios的拦截器，是由两个数组维护的，都是Promise对象，其中一个数组按顺序用来存储 触发请求的Promise、request的拦截器的Promise。另一个数组按顺序存储response的拦截器的Promise。最终利用Promise的链式调用的特性，生成一个Promise。因此执行一次axios请求，都会按顺序执行 触发请求的Promise、request的拦截器的Promise、response的拦截器的Promise。


## Reference

1. [axios](https://github.com/axios/axios/blob/master/lib/core/Axios.js)

