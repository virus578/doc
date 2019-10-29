# 概念

webpack是js应用程序的静态文件模块的打包器 webpack处理程序 递归构建一个关系依赖图, 其中包含需要的每个模块 然后把模块打包为一个或者多个bundle

特点:高度的可配置的 

四个核心概念: 入口 输出 loader 插件

入口:wepack指定使用哪个模块作为构建其内部依赖图的的开始,进入入口,webpack就会找出那些模块和库是(直接间接)依赖的

entry属性 指定一个或者或者多个出口 默认值为./src

```js
module.exports = {
  entry: './path/to/my/entry/file.js'
};
```

出口:webpack在哪里创建bundles,以及如何命名这些文件,

output属性 默认值为./dist

```js
const path = require('path');

module.exports = {
  entry: './path/to/my/entry/file.js',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'my-first-webpack.bundle.js'
  }
};
```

loader:让webpack处理非js文件(webpack自身只理解js),

load将所有类型文件 转换为程序的依赖图(bundles)可以直接应用的模块

webpackloader的两个目标

1. `test` 属性，用于标识出应该被对应的 loader 进行转换的某个或某些文件。
2. `use` 属性，表示进行转换时，应该使用哪个 loader。

```js
const path = require('path');

const config = {
  output: {
    filename: 'my-first-webpack.bundle.js'
  },
  module: {
    rules: [
      { test: /\.txt$/, use: 'raw-loader' }
    ]
  }
};

module.exports = config;
```

插件

loader转换某些类型的文件 插件执行更广的任务 从优化到压缩 再到重新定义环境变量

如何使用一个插件 require() 然后 添加到plugin中 

多数插件可以选项(option)自定义

你可以在一个配置文件为了不同目的多次使用同一个插件 使用new 操作符 来创建它的一个实例

```js
const HtmlWebpackPlugin = require('html-webpack-plugin'); // 通过 npm 安装
const webpack = require('webpack'); // 用于访问内置插件

const config = {
  module: {
    rules: [
      { test: /\.txt$/, use: 'raw-loader' }
    ]
  },
  plugins: [
    new HtmlWebpackPlugin({template: './src/index.html'})
  ]
};

module.exports = config;
```

模式

 `development`    production   来设置 `mode` 参数，你可以启用相应模式下的 webpack 内置的优化 

```js
module.exports = {
  mode: 'production'
};
```



# 入口起点(entry  point)

# 输出(output)

# 模式(mode)

# loader

# 插件(plugins)

# 配置(configuration)

# 模块(modules)

# 模块解析(modules resolution)

# 依赖图(dependence graph)

# mamifest

# 构建目标(targets)

# 模块热替换(hot module replacement)