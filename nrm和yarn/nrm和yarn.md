```sh
#nrm
----
#https://segmentfault.com/a/1190000000473869#articleHeader6
#如何搭建私有NPM仓库
#https://cnodejs.org/topic/5338c5db7cbade005b023c98
#https://segmentfault.com/a/1190000000368906
npm install -g nrm
nrm ls 查看所有源
nrm use tabao 使用淘宝源
nrm test npm 测试向对应的源
nrm test 测试所有源
nrm del <register> 删除源
nrm add <register> <url> [home] 添加源
```

```shell
#yarn 如果你以前安装过某个包，再次安装时可以在没有任何互联网连接的情况下进行。
#网络性能 队列方式
#扁平模式: 将依赖包的不同版本归结为单个版本，以避免创建多个副本。
#网络弹性:重试机制确保单个请求失败并不会导致整个安装失败。
---
#初始化一个新项目
yarn init
#安装项目的全部依赖
yarn 
#安装包
yarn add [package] 
yarn add[package]@[version]
yarn add [package]@[tag]
#升级依赖包
yarn upgrade [package]
yarn upgrade [package]@[version]
yarn upgrade [package]@[tag]
#移除包
yarn remove [pakage]
```

