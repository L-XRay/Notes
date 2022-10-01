# 构建工程完成RPC接口的实现和调用

## 模块分层

1. application，应用层，引用：`domain`
2. domain，领域层，引用：`infrastructure`
3. infrastructure，基础层，引用：`无`
4. interfaces，接口层，引用：`application`、`rpc`
5. rpc，RPC接口定义层，引用：`common`
6. common，通用包，引用：`无`

## 模块关系

1. 首先 rpc 层定义接口，供接口层实现以及外部调用。
2. 基础层 提供数据的仓储服务，供领域服务或微服务外的应用服务调用接口实现数据的持久化以及资源的直接访问，降低外部资源对业务逻辑的影响。
3. 领域层 主要封装核心的业务逻辑，供应用层调用接口实现编排、组合以及事件订阅发布等。
4. 接口层 实现 rpc 层的接口，调用应用层编排好的服务接口将用户的请求处理并返回给外部调用方。

ps：这里只简单测试调用 rpc ，因此这里 接口层直接引入基础层仓储服务进行测试。

![step02.drawio](/Users/ray/Notes/抽奖系统/images/step02.drawio.png)