# NOTE.md

先学习一下示例的代码

### 包 react-scripts

This package includes scripts and configuration used by Create React App.

create-react-app 是一个全局的命令行工具用来创建一个新的项目

react-scripts 是一个生成的项目所需要的开发依赖

一般我们开始创建 react web 应用程序的时候,要自己通过 npm 或者 yarn 安装项目的全部依赖，再写 webpack.config.js,一系列复杂的配置,搭建好开发环境后写 src 源代码。
现在 如果你正在搭建 react 运行环境，使用 create-react-app 去自动构建你的 app 程序。你的项目所在的文件夹下是没有配置文件。react-scripts 是唯一的 额外的 构建依赖在你的 package.json 中，你的运行环境将有每一个你需要用来构建一个现代 React app 应用程序。你需要的依赖，和在配置文件中编写的配置代码，react-scripts 都帮你写了，比如：react-scripts 帮你自动下载需要的 webpack-dev-server 依赖，然后 react-scripts 自己写了一个 nodejs 服务端的脚本代码 start.js 来 实例化 WebpackDevServer ，并且运行启动了一个使用 express 的 Http 服务器，现在你只需要专心写 src 源代码就可以了。省去了很多精力，最适合快速上手一个 demo 了。

### enzyme

React 测试必须使用官方的测试工具库，但是它用起来不够方便，所以有人做了封装，推出了一些第三方库，其中 Airbnb 公司的 Enzyme 最容易上手。

## API

http://www.redux.org.cn/docs/react-redux/api.html

### Provider

<Provider store> 使组件层级中的 connect() 方法都能够获得 Redux store。正常情况下，你的根组件应该嵌套在 <Provider> 中才能使用 connect() 方法。

#### 传入方式

1. 把根组件嵌套在 <Provider> 中。
2. 把 store 作为 props 传递到每一个被 connect() 包装的组件。

### connect 详解，似乎就是 mobx 的 inject 步骤

connect([mapStateToProps], [mapDispatchToProps], [mergeProps], [options])

连接 React 组件与 Redux store。
连接操作不会改变原来的组件类（由原来的生成一个新的）。反而返回一个新的已与 Redux store 连接的组件类。

究竟 connect 方法到底做了什么，我们来一探究竟。

首先看下函数的签名：

connect() 接收四个参数，它们分别是 mapStateToProps，mapDispatchToProps，mergeProps 和 options。

mapStateToProps(state, ownProps) : stateProps

这个函数允许我们将 store 中的数据作为 props 绑定到组件上。

### 以视图区域来切分 reducers

### Webpack DefinePlugin 使用

DefinePlugin 插件可以从打包运行的 node 环境给代码注入变量

[使用参考文档](https://www.jianshu.com/p/887f0454ef96)
