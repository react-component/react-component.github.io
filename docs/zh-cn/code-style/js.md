# js 编码规范

代码通过 eslint（在根目录运行 `npm run lint`），具体规范参见: https://github.com/airbnb/javascript


## 文件命名

- js 模块采用 es2015 格式，主体代码放在 src 目录下，根目录 index.js 仅引用 src 下相关文件
- 若用到了 jsx 语法或 es6 特性，文件后缀名请改做 jsx，文件内请不要包含 `/** @jsx React.DOM */`
- src 目录模块如果返回值是个类，则文件名首字母大写
- 测试用例文件名以 .spec.js(jsx) 结尾
- 测试用例文件名推荐和 src 下源码对应，比如 src/Calendar.jsx 对应于 tests/Calendar.spec.jsx
- 测试用例入口文件名为 index.spec.js，推荐里面只应 import 其他测试用例

## 代码格式

- 生成 React 组件类使用 React.createClass,不要使用 es6 class, es6 class 无法实现 mixin 功能, 并且不能自动绑定
 ```js
   var Component = React.createClass({
     onClick() {
       // ...
     },
     render() {
       return <div onClick={this.onClick}/>;
     }
   });
 ```
- log 可以使用 https://www.npmjs.com/package/warning
- 公共包通过 npm install 后，js 中可以 import node_modules 下的公共包 js，但不可以 import css
- 使用 propType 制定 react 组件属性的类型
- 只能 import 'react' 不可以 import 'react/lib/xx'
- 禁止使用 jquery 等大而全的类库
- React 类必须用一个变量声明

Menu.js
```js
import React from 'react';
var Menu = React.createClass({
  propTypes: {
    active: React.PropTypes.bool
  }
});
export default Menu;
```

- 组件根节点样式名默认为 rc- 加上小写组件名，组件名单词间以 - 分隔，允许通过 prefixCls 定制
- 组件内部的样式名都要以 prefixCls 为前缀
- 组件允许用户通过 className 定制样式名

```js
var Menu = React.createClass({
  render: function(){
    var prefixCls = this.props.prefixCls;
    var className = prefixCls || "rc-menu";
    if(this.props.className){
      className += ' '+this.props.className;
    }
    return (<div className={className}> <span className={prefixCls + "-title"}></span> TODO</div>);
  }
});
```

- 组件是 react-component 而不是 react-bootstrap，不要把一些 bootstrap 的样式生搬过来，例如

```js
var Dialog = React.createClass({
  render: function(){
    return <div className='modal-dialog rc-dialog'>
      <div className='rc-dialog-header modal-header'></div>
    </div>
  }
});
```

组件和 bootstrap css 绑定过紧，样式和 js 不一致，建议通过属性来解决：

```js
var Dialog = React.createClass({
  render: function(){
    var prefixCls = this.props.prefixCls;
    return <div className={prefixCls}>
      <div className={prefixCls + "-header"}></div>
    </div>
  }
});

<Dialog prefixCls="modal" />
```

## 参考

- https://github.com/aralejs/aralejs.org/wiki/UI-%E7%BB%84%E4%BB%B6%E8%87%AA%E5%AE%9A%E4%B9%89%E6%A0%B7%E5%BC%8F
- https://github.com/aralejs/aralejs.org/wiki/JavaScript-编码风格
- https://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml
