# react 组件代码规范
---

author: yiminghe@gmail.com

## 细则

### 总体

- 使用 generator-rc, rc-tools, rc-server 基础设施
- 组件需要支持 travis, coveralls, saucelabs, npm, spm
- 组件功能点需要有测试用例，示例，js 源码，可选的 css 源码

### js 源码

- js 模块采用 commonjs 格式，主体代码放在 lib 目录下，根目录 index.js 仅引用 lib 下相关文件
- 公共包通过 npm install 后，js 中可以 require node_modules 下的公共包 js，但不可以 require css
- 模块如果返回值是个类，则文件名大写
- React 类必须用一个变量声明

Menu.js
```js
var React = require('react');
var Menu = React.createClass({
});
module.exports = Menu;
```

- 组件根节点样式名为 rc- 加上小写组件名，组件名单词间以 - 分隔
- 组件允许用户通过 className 添加自己的样式名

```js
var Menu = React.createClass({
  render: function(){
    return (<div className="rc-menu {this.props.className}">TODO</div>);
  }
});
```

### css 源码

- 样式采用 less 语法
- less 中通过 import "xx/xx.css" 可以引用通过 npm install 后公共包 xx 内的 css
- bootstrap 有的直接用 bootstrap，bootstrap 没的自己写在 assets/bootstrap.less 中

### examples

- examples 格式为 md，通过 ````js ````html 引入高亮并执行的代码，通过 ```js ```html 仅引入高亮的代码
- examples 引入 bootstrap 样式，通过配置组件的 className 使用 bootstrap 样式

```
<link href="/node_modules/bootstrap/dist/css/bootstrap.css?nowrap"/>
<div id="react-content"></div>

React.render(<Menu className = "nav-bar nav"></Menu>, document.getElementById('react-content'));

```

### tests

- 代码位于 tests/xx-spec.js index-spec.js 为必须，里面可以 require 其他 spec
- 测试用例 js 采用 commonjs 格式，可以 require node_modules 下的公共包的 js 和 css
- 测试框架为 mocha，断言库为 expect.js

## 示例

以上规则示例参考： https://github.com/react-component/calendar
