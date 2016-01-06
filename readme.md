# APS 使用教程

自动化量产系统（Automated Production System，以下简称 APS）是前端技术部推出的一套高效地开发产品的解决方案。针对产品开发的每个环节，APS 都有相应的工具做一些规范化以及自动化的工作，大大地提升了工作效率和降低了沟通成本。

下面介绍 APS 的基本用法。


#### 第一步，在接口管理平台（以下简称 NEI）上创建一个项目

1. 打开 [NEI](http://nei.hz.netease.com/)，使用 corp 邮箱登录。
2. 创建项目，根据需求创建页面、异步接口、数据类型等资源，具体用法请查看 [NEI 帮助](http://nei.hz.netease.com/manual/)。


#### 第二步，使用 NEI 构建工具生成项目模板代码

###### 安装 NEI 构建工具

NEI 构建工具基于 [Node.js](http://nodejs.org/) 平台，请先安装 Node.js 环境。注意，Node.js 版本须为 `v4.2` 及以上。

1. 执行下面的命令安装构建工具

    ```bash
    npm install nei –g
    ```

2. 执行下面的命令，创建项目的模板代码。pid 为第一步创建的项目的 id。其他命令及参数配置请查看构建工具的说明文档：[NEI 构建工具](https://github.com/genify/nei)。

	```bash
	nei build [pid]
	```    

3. 下面以 windows 电脑为例，生成 `NEI 后台管理系统` 项目。默认生成的项目会放在执行 `nei build` 命令时所在的根目录。假如希望将生成的模板代码放在 `D:\workspace\neibms` 目录中，先在命令提示符中进到 D 盘根目录，然后执行下面的命令：

```bash
cd workspace\neibms
```

```bash
nei build 11112
```

其中，11112 是 `NEI 后台管理系统` 项目的 id。

如果执行上面的命令时没有错误发生，最后会提示 `build success`，说明工程已经创建成功。打开 `D:\workspace\neibms`  目录，可以看到项目的结构和一些模板代码及配置文件已经自动生成。

下面以前端工程师的视角，介绍本地模拟容器 [Puer](https://github.com/leeluolee/puer) 的基本用法。

#### 第三步，安装 Puer

1. 
