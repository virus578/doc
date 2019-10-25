npm从5.2开始加入了 npx命令

npm自带npx命令 如果出问题就 npm install -g npx

-  调用项目安装的模块

  ```
  一般来说，调用 Mocha ，只能在项目脚本和 package.json 的scripts字段里面， 如果想在命令行下调用，必须像下面这样。
  
  
  # 项目的根目录下执行
  $ node-modules/.bin/mocha --version
  
  npx mocha --version
  ```

  

- 避免全局安装

  ```
  create-react-app这个模块是全局安装，npx 可以运行它，而且不进行全局安装
  npx create-react-app my-react-app
  npx 将create-react-app下载到一个临时目录，使用以后再删除。所以，以后再次执行上面的命令，会重新下载create-react-app。
  2.--no-install 参数和--ignore-existing 参数
  如果想让 npx 强制使用本地模块，不下载远程模块，可以使用--no-install参数。如果本地不存在该模块，就会报错。
  $ npx --no-install http-server
  
  如果忽略本地的同名模块，强制安装使用远程模块，可以使用--ignore-existing参数。比如，本地已经全局安装了create-react-app，但还是想使用远程模块，就用这个参数。
  $ npx --ignore-existing create-react-app my-react-app
  ```

  

- 使用不同版本的node 原理就是从npm下载node 使用后再删掉 某些场景比nvm 版本管理器方便

  

  