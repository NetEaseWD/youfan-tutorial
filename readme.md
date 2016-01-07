# APS 使用教程

自动化量产系统（Automated Production System，以下简称 APS）是前端技术部推出的一套高效地开发产品的解决方案。针对产品开发的每个环节，APS 都有相应的工具做一些规范化以及自动化的工作，大大地提升了工作效率和降低了沟通成本。

本文介绍 APS 的基本用法。

#### 第一步，在接口管理平台（以下简称 NEI）上创建一个项目

1. 打开 [NEI](http://nei.hz.netease.com/)，使用 corp 邮箱登录。

2. 创建项目，根据需求创建页面、异步接口、数据类型等资源，具体用法请查看 [NEI 帮助](http://nei.hz.netease.com/manual/)。


#### 第二步，使用 NEI 构建工具生成项目模板代码

NEI 构建工具基于 [Node.js](http://nodejs.org/) 平台，请先安装 Node.js 环境。

>注意，Node.js 版本须为 `v4.2` 及以上。

1. 运行下面的命令安装构建工具：

    ```bash
    npm install –g nei
    ```

    如果已安装过构建工具，则可以运行下面的命令将构建工具更新至最新版本：

    ```bash
    npm update –g nei
    ```

2. 运行下面的命令，创建项目的模板代码。pid 为第一步创建的项目的 id。其他命令及参数配置请查看构建工具的说明文档：[NEI 构建工具](https://github.com/genify/nei)。

	```bash
	nei build [pid]
	```    

3. 下面以 windows 电脑为例，生成 `NEI 后台管理系统` 项目。默认生成的项目会放在执行 `nei build` 命令时所在的根目录。假如希望将生成的工程文件放在事先创建好的 `D:\workspace\neibms` 目录中，先在命令提示符中进到 D 盘根目录，然后运行下面的命令：

  ```bash
  cd workspace\neibms
  ```

  ```bash
  nei build 11112
  ```

其中，11112 是 [`NEI 后台管理系统`](http://nei.hz.netease.com/main#/m/project/page/?pid=11112) 项目的 id。

如果运行上面的命令时没有错误发生，最后会提示 `build success`，说明工程已经创建成功。打开 `D:\workspace\neibms`  目录，可以看到项目的结构和一些配置文件已经自动生成：

  ```bash
├── deploy
├── nei.11112
└── src
    └── main
        └── webapp
            ├── WEB-INF
            │   └── views
            │       └── common
            ├── res
            └── src
                ├── css
                ├── javascript
                │   ├── lib
                │   └── widget
                └── mcss
  ```

下面以前端工程师的视角，介绍本地模拟容器 [Puer](https://github.com/leeluolee/puer) 的基本用法，不过首先需要安装前端依赖的资源文件。

#### 第三步，使用 Bower 安装前端依赖资源
首先，进到目录 `src\main\webapp\` 中，该目录中有一个 `bower.json` 文件，里面已经事先定义好了一些依赖，我们需要使用 Bower 工具来安装这些依赖。

1. 运行下面的命令安装 Bower

  ```bash
  npm install –g bower
  ```

2. 然后运行下面的命令安装依赖：

  ```bash
  bower install
  ```

3. 由于 bower 只负责下载在 `bower.json` 文件中定义的依赖，并不会解析 Node.js 项目中的依赖，所以需要进到目录 `/src/main/webapp/src/javascript/lib/express-freemarker` 中运行下面的命令：

  ```bash
  npm install
  ```

>注意，上面的步骤需要根据具体的项目进行具体的操作，本文演示的都是默认情况，nei 构建工具默认生成的是 Java 工程，默认 的模板引擎是 freemarker。此外，运行该模板引擎需要安装 [`JDK`](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)，请根据实际情况自行安装。


#### 第四步，使用 Puer 进行本地开发

1. 运行下面的命令安装 Puer：

  ```bash
  npm install –g "leeluolee/puer#next"
  ```

2. 进到 `D:\workspace\neibms` 目录，运行下面的命令：

  ```bash
  puer -c nei.11112\puer.js
  ```

此时，puer 会将当前目录作为静态服务器，并会在浏览器中打开 [http://localhost:8002/](http://localhost:8002/)。

接下来，就可以进行开发了。比如，在 NEI 中定义了页面 `首页`，它的访问路径是 `/index`，则它的访问地址便是：[http://localhost:8002/index](http://localhost:8002/index)。

Good luck!
