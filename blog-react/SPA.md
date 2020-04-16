
## 什么是单页面应用(SPA)

- 单页面应用(SPA)是指用户在浏览器**加载单一的 HTML 页面**，**后续请求都无需再离开此页**
- 目标：旨在用为用户提供了**更接近本地移动 APP** 或桌面应用程序的体验，提高性能。
- 流程：第一次请求时，将导航页传输到客户端，其余请求通过 REST API 获取 JSON 数据
- 实现：数据的传输通过 Web Socket API 或 RPC(远程过程调用)。

### SPA 的优缺点

- 优点：用户体验流畅，服务器压力小，前后端职责分离
- 缺点：关键词布局难度加大，不利于 SEO

### SPA、单页面应用重新部署后，正在浏览的页面如何更新缓存

这里的这个问题，主要是当前项目已发，但是用户正在使用，**这个时候 html 文件如果不去主动刷新，是不会请求到最新的 html 的，也就不可能会有最新的 js，css 了**。所以这个时候，怎么检测最新版本并且刷新页面就显得很重要。

对于一般的发布，修改 js 与 css 的 hash 值，html 不会缓存，所以一般都是可以拿到最新的修改的。

目前临时解决方案有两个：接口和文件记录

- 通过**后端接口返回版本号判断是否有更新**，有更新，就把页面刷新一下。这个事情可以放到切换路由的时候做，比如 beforeEach，就是每次请求都查询，需要后端配合。
- 在编译的时候**自己生成一个 js 文件**，然后前端用 jsonp 去请求这个 js，**判断是否有更新。有更新，就把页面刷新一下**。这个事情可以放到切换路由的时候做，比如 beforeEach。这个时候可以添加到每次的接口请求之前请求一下这个文件，或者使用定时的模式，到时间主动去请求，与 electron 的更新很类似。