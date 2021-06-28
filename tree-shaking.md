# tree-shaking


## tree-shaking定义

tree-shaking本质是去除项目中无用代码消除。
DCE(dead code elimination): 无用代码消除在传统的编程语言编译器中，编译器可以判断出哪些代码不影响输出，然后消除这些代码，这个称谓
tree-shaking是DCE一种新的实现。JavaScript同其他编程语言不同，JavaScript绝大部分情况是需要通过网络加载，文件的大小决定加载效率。因此消除无用的代码对js来说非常有意义。

## DCE

传统DCE消除无用代码，tree-shaking关注与消除没有用到的代码

DEC:
  1. 代码不会被执行，不可达
  2. 代码的执行结果没有用到
  3. 代码只影响死变量`只读不写`
## tree-shaking原理

tree-shaking的消除原理是依赖于ES6的模块特性

1. 只能作为模块顶层的语句出现
2. import的模块名只能是字符串常量
3. import binding是imutable

## 组件按需引入

## REFRENCE

1. [你的Tree-Shaking并没什么卵用](https://juejin.cn/post/6844903549290151949#heading-0)

> 这篇清晰讲解了为什么像elementUI之类的一些组件库，不能直接利用webpack的tree-shaking实现按需引入。而是引用第三方babel插件[babel-plugin-component](https://github.com/ElementUI/babel-plugin-component)才能实现其效果。

2. [从 Babel 到组件按需引入原理](https://juejin.cn/post/6844904138073980942#heading-9)

> 这篇主要babel插件实现按需引入的原理

3. [Tree-Shaking性能优化实践 - 原理篇](https://zhuanlan.zhihu.com/p/32554436?hmsr=toutiao.io&utm_medium=toutiao.io&utm_source=toutiao.io)

4. [小红书面试官：介绍一下 tree shaking 及其工作原理](https://segmentfault.com/a/1190000038962700)

5. [深入 Webpack 的 Tree Shaking](https://juejin.cn/post/6866747701908733966)

> 这篇从实践的角度描述了webpack的tree-shaking的原理

6. [wikipedia|Tree shaking](https://en.wikipedia.org/wiki/Tree_shaking)

> tree shaking的定义。tree-shaking 和 dead code elimination 不是同一个东西