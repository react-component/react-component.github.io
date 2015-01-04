# react 组件代码规范
---

author: yiminghe@gmail.com

## 细则

### 总体

- 使用 generator-rc, rc-tools, rc-server 基础设施
- 组件需要支持 travis, coveralls, saucelabs, npm, spm
- 组件功能点需要有测试用例，示例，js 源码，可选的 css 源码

### js 源码

详见 [js 源码规范](./code-style/js.md)

### js 注释

详见 [js 注释规范](./code-style/comment.md)

### css 源码

详见 [css 源码规范](./code-style/css.md)

### examples

- examples 格式为 md，通过 \`\`\`\`js \`\`\`\`html 引入高亮并执行的代码，通过 \`\`\`js \`\`\`html 仅引入高亮的代码
- \`\`\`\`js 中的 js 代码为 commonjs 格式，第一行为注释 `/** @jsx React.DOM */`
- examples 引入 bootstrap 样式，通过配置组件的 className 使用 bootstrap 样式

```
<link href="/node_modules/bootstrap/dist/css/bootstrap.css?nowrap"/>

\````html
<div id="react-content"></div>
\````

\````js
/** @jsx React.DOM */
React.render(<Menu className = "nav-bar nav"></Menu>, document.getElementById('react-content'));
\````

```

### tests

- 代码位于 `tests/xx-spec.js` `index-spec.js` 为必须，里面可以 require 其他 spec
- 测试用例 js 采用 commonjs 格式，可以 require node_modules 下的公共包的 js 和 css
- 可以 require('react') 以及 require('react/addons')
- 测试框架为 mocha，断言库为 expect.js

## 示例

以上规则示例参考： https://github.com/react-component/calendar
