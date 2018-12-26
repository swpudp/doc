##dotnet core请求管道
对http上下文的一系列处理。监听到请求->处理上下文->响应。监听到http请求后，在Configure方法指定使用什么方式处理请求,如UseMvc()代表使用MVC处理请求。
##dotnet core之前
以前.NET FRAMEWORK全家桶，什么都给你默认实现了，开发只用去指定位置添加指定规则的代码，开发者完全没有思考请求是怎么处理的，怎么达到你的方法的，以至于.NET被称为入门简单，但技术含量低，很难精通。可以快速开发，但是缺乏深度，缺乏扩展，缺乏优化空间。
##dotnet core设计理念
组件化开发，一切组件都要组装和配置到请求管道中，才能使用。
##中间件Middleware
IApplicationBuilder：应用程序构建者->Build()->应用程序的实例->用中间件组装一个Application处理流程（多个委托串联起来）

执行流程,假如三个middleware，处理请求和响应请求过程如下：middleware1 start->middleware2 start->middleware3 start->middleware3 response->middleware2 response->middleware1 response，戏称<俄罗斯套娃>。
![](https://i.imgur.com/lAWLjK0.png)
中间件设计完全没有预定义。
next()前为响应前执行的逻辑，next()后为响应后执行的逻辑。
新管道处理模型，一切都可以定制，任意环节都可以扩展。