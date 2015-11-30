# react 组件代码规范
---

author: yiminghe@gmail.com

## 细则

### 总体

- 使用 generator-rc, rc-tools, rc-server 基础设施
- 组件需要支持 travis, coveralls, saucelabs, npm
- 组件功能点需要有测试用例，示例，js 源码，可选的 css 源码

### js 源码

详见 [js 源码规范](./code-style/js.md)

### js 注释

详见 [js 注释规范](./code-style/comment.md)

### css 源码

详见 [css 源码规范](./code-style/css.md)

### examples

- examples 中的 html 不可修改，通过 js 中的 jsx 渲染页面，通过 import css 引入 css
- \`\`\`\`js 中的 js 代码为 es2015 格式

```js
\````js
import 'rc-menu/assets/index.less';
var Menu = require('rc-menu');
React.render(<Menu className = "nav-bar nav"></Menu>, document.getElementById('react-content'));
\````
```

通过 npm run pub 来发布 npm 以及 demo, 例如 http://react-component.github.io/calendar/

### tests

- 代码位于 `tests/xx.spec.js` `index.spec.js` 为必须，里面可以 import 其他 spec
- 测试用例 js 采用 es2015 格式，可以 import node_modules 下的公共包的 js 和 css
- 测试框架为 mocha，断言库为 expect.js

## 示例

以上规则示例参考： https://github.com/react-component/calendar
