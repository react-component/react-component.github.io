# 如何写一个 react 组件
---

author: yiminghe@gmail.com

## 建立组件 git 库

- https://github.com/react-component

## 搭建脚手架

- 使用 https://github.com/react-component/generator-rc 搭建脚手架

## 源码

- 在 lib 目录中写 js，在 assets 目录下 css，在 tests 目录下写 测试用例，规范参考 [react 组件代码规范](./rc-component-code-style.md).
- 开发中用到其他公共库，通过 npm install --save 以及 npm install --save-dev 来安装

## 启用开源平台服务

### travis-ci

访问 http://https://travis-ci.org/profile 开启对应 git 库

### coveralls.io

访问 https://coveralls.io/repos/new 开启对应 git 库

### saucelabs.com

- 访问 https://saucelabs.com/opensauce 注册对应 npm 包名的账号，
- 以该账号登陆后，访问 https://docs.saucelabs.com/ci-integrations/travis-ci/
- 在库根目录执行 gem install travis 和之后的两个 travis encrypt 命令

## 开发调试

- 在项目根目录执行 npm install
- 在项目根目录执行 npm start
- 打开 http://localhost:xxxx 访问库, xxxx 为脚手架配置的网络端口
- 打开 http://localhost:xxxx/examples/index.md 查看示例
- 打开 http://localhost:xxxx/tests/runner.html 运行测试

## 支持 spm

- 修改 package.json 将源码中用到的库，从 dependencies 字段复制到 spm 字段

```js
{
  "dependencies":{
    "react": "0.12.x"
  },
  "spm":{
    "dependencies":{
      "react": "0.12.x"
    }
  }
}
```

## 支持 HISTORY.md

- 通过在根目录运行 npm run history 生成 HISTORY.md
- 需要建立必要的 milestone，issue，label，参见： https://github.com/yiminghe/gh-history
- milestone 标题为语义化版本好，issue 属于某个 milestone，并且具备 label
- label 为枚举，包括
 - `new` 新增的属性、功能、方法、特性等等
 - `fixed` 修复 bug 和影响使用的性能问题等
 - `improved` 接口增强、健壮性和性能提升、代码优化、依赖模块升级等。
 - `changed` 涉及到兼容性变化的改动。

## 发布

- 在根目录运行 npm publish
