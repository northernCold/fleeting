# tree-shaking


## tree-shaking定义

tree-shaking是一种`dead code elimination`技术，主要是优化项目中的代码（消除项目中无用的代码）。

> JavaScript同其他编程语言不同，JavaScript绝大部分情况是需要通过网络加载，文件的大小决定加载效率。因此消除无用的代码对js来说非常有意义。
## tree-shaking vs dead code elimination

tree-shaking与传统`dead code elimination`的区别：

|      |   目的   |   如何实现   |
| ---- | ---- | ---- |
|   dead code elimination   |   消除项目中的不影响结果的代码`dead code`（包含：1.永远执行不到的代码；2.代码只影响死变量`只读不写`）<sub>\[1\]</sub>   |   标记`dead code`，然后消除   |
|   tree-shaking  |   消除项目中没有用到的代码   |   从入口开始，只包含可执行的函数，剩下的都是没有用到的代码。又称为 `live code inclusion`<sub>\[2\]</sub>   |

## tree-shaking原理

tree-shaking的消除原理是依赖于ES6的模块特性。<sub>\[3\]</sub>

1. 只能作为模块顶层的语句出现
2. import的模块名只能是字符串常量
3. import binding是imutable

使其静态分析代码成为可能。ES的依赖关系是确定的，与运行时的状态无关。

webpack中在编译代码的过程中，会标记未使用到的代码。然后代码压缩的时候，会删除标记的代码。<sub>\[4\]</sub>

## 副作用

如果一个函数修改了外部环境的状态，则称该函数具有副作用。

在实际中，在使用组件库中tree-shaking并没有作用[[]]
## 组件按需引入

[[组件库如何做到按需引入]]

## REFRENCE

1. [Dead code elimination](https://en.wikipedia.org/wiki/Dead_code_elimination)
> tree shaking的定义。tree-shaking 和 dead code elimination 不是同一个东西

2. [Tree shaking](https://en.wikipedia.org/wiki/Tree_shaking)

3. [Tree-Shaking性能优化实践 - 原理篇](https://zhuanlan.zhihu.com/p/32554436?hmsr=toutiao.io&utm_medium=toutiao.io&utm_source=toutiao.io)

4. [深入 Webpack 的 Tree Shaking](https://juejin.cn/post/6866747701908733966)

5. [Webpack 中的 sideEffects 到底该怎么用？](https://github.com/kuitos/kuitos.github.io/issues/41)
> 这篇从实践的角度描述了webpack的tree-shaking的原理

6. [你的Tree-Shaking并没什么卵用](https://juejin.cn/post/6844903549290151949#heading-0)

> 这篇清晰讲解了为什么像elementUI之类的一些组件库，不能直接利用webpack的tree-shaking实现按需引入。而是引用第三方babel插件[babel-plugin-component](https://github.com/ElementUI/babel-plugin-component)才能实现其效果。

7. [从 Babel 到组件按需引入原理](https://juejin.cn/post/6844904138073980942#heading-9)

> 这篇主要babel插件实现按需引入的原理

8. [小红书面试官：介绍一下 tree shaking 及其工作原理](https://segmentfault.com/a/1190000038962700)
