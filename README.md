<<<<<<< HEAD
# 简聊开源版

[简聊](https://jianliao.com)所有业务代码的开源版本，可作任意修改

[简聊 - 产品](http://tburl.in/c888ede0/)项目包含了简聊由开始到现在的所有开发历程，设想，和设计资源，感兴趣的同学可加入项目参观或留言

## 部署

- Node 4 (`nvm use`)
- Npm 2

### 安装环境

- 简聊使用 MongoDB 作为数据库，Redis 作为缓存和消息通讯中间件。所以首先需要在本地部署 [MongoDB](https://www.mongodb.org/) 和 [Redis](http://redis.io/) 并使用默认端口号（配置文件见 config/default.coffee）。建议使用 MongoDB 3.2 和 Redis 2.8，更高版本未经过生产环境测试。
- 简聊的搜索使用 [ElasticSearch 1.6.2](https://www.elastic.co/) + [ik 中文分词插件](https://github.com/medcl/elasticsearch-analysis-ik)，代码中已经关闭了消息搜索的功能，如需打开，需要修改以下文件

  ```
  - talk-api2x/
  - server/
   - schemas/
     - search-favorite.coffee      # 删除 `return # @osv`
     - search-message.coffee       # 删除 `return # @osv`
     - search-story.coffee         # 删除 `return # @osv`
     - message.coffee              # 删除 `return # @osv`
     - favorite.coffee             # 删除 `return # @osv`
   - observers/
     - story.coffee                # 删除 `return # @osv`
  ```

- 并且在 `config/default.coffee` 中增加

  ```
  searchHost: 'localhost'
  searchPort: 9200
  searchProtocol: 'http'
  ```

- 执行 [create-search-template.sh](talk-api2x/scripts/create-search-template.sh) 创建索引结构

### 安装代码依赖

1. 初始化安装依赖 `npm run init`
2. 执行代码 `npm start`
3. 访问浏览器 `http://localhost:7001`

## LICENSE

[MIT](./LICENSE)
=======
Nodeclub
=

[![build status][travis-image]][travis-url]
[![codecov.io][codecov-image]][codecov-url]
[![David deps][david-image]][david-url]
[![node version][node-image]][node-url]

[travis-image]: https://img.shields.io/travis/cnodejs/nodeclub/master.svg?style=flat-square
[travis-url]: https://travis-ci.org/cnodejs/nodeclub
[codecov-image]: https://img.shields.io/codecov/c/github/cnodejs/nodeclub/master.svg?style=flat-square
[codecov-url]: https://codecov.io/github/cnodejs/nodeclub?branch=master
[david-image]: https://img.shields.io/david/cnodejs/nodeclub.svg?style=flat-square
[david-url]: https://david-dm.org/cnodejs/nodeclub
[node-image]: https://img.shields.io/badge/node.js-%3E=_4.2-green.svg?style=flat-square
[node-url]: http://nodejs.org/download/

## 介绍

Nodeclub 是使用 **Node.js** 和 **MongoDB** 开发的社区系统，界面优雅，功能丰富，小巧迅速，
已在Node.js 中文技术社区 [CNode(http://cnodejs.org)](http://cnodejs.org) 得到应用，但你完全可以用它搭建自己的社区。

## 安装部署

*不保证 Windows 系统的兼容性*

线上跑的是 [io.js](https://iojs.org) v2.3.3，[MongoDB](https://www.mongodb.org) 是 v2.6，[Redis](http://redis.io) 是 v2.8.9。

```
1. 安装 `Node.js/io.js[必须]` `MongoDB[必须]` `Redis[必须]`
2. 启动 MongoDB 和 Redis
3. `$ make install` 安装 Nodeclub 的依赖包
4. `cp config.default.js config.js` 请根据需要修改配置文件
5. `$ make test` 确保各项服务都正常
6. `$ node app.js`
7. visit `http://localhost:3000`
8. done!
```

## 测试

跑测试

```bash
$ make test
```

跑覆盖率测试

```bash
$ make test-cov
```

## 贡献

有任何意见或建议都欢迎提 issue，或者直接提给 [@alsotang](https://github.com/alsotang)

## License

MIT
>>>>>>> upstream/master
