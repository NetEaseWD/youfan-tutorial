# Puer 简介

[Puer](https://github.com/leeluolee/puer) 是一个本地模拟容器。在使用 [NEI 构建工具](https://github.com/genify/nei)生成项目的时候，会自动生成 Puer 的配置文件。

Puer 的基本使用方法，在 [APS 使用教程](readme.md) 中已经有过介绍，在此不再赘述。如果想深入了解，请查看它的[官方文档](https://github.com/leeluolee/puer)。

在前端开发的时候，除了异步接口调用之外，还有很多的 form 表单提交。form 表单提交一般会有多种状态，譬如 `成功`、`失败`等，不同的状态会有不同的提示信息。

下面介绍一下如何使用 Puer 来模拟普通的 form 表单提交。

请先按照 [APS 使用教程](readme.md) 中的操作步骤创建项目，项目 id 为 `11133`。

使用编辑器打开文件 `/src/main/webapp/WEB-INF/views/index.ftl`，添加下面的内容：

```html
<form action="/form" method="GET">
    <input type="submit" value="submit" />
</form>
```

打开页面：[http://localhost:8002/index](http://localhost:8002/index)，此时点击 `submit` 按钮，页面会跳转到成功页面（请看页面标题）。

使用编辑器打开文件 `/nei.11133/route.js`，它的内容如下：

```javascript
var u = require('./util.js');

module.exports = {
    "GET /form":u.r(0,[{"i":10760,"p":"submit/success"},{"i":10761,"p":"submit/error"}]),
    "GET /index":u.r(0,[{"i":10762,"p":"index"}])
};
```

我们可以发现，以 `GET` 方式请求页面 `/form` 的时候，默认返回的是 `submit/success` 这个模板，返回哪个模板由第一个参数指定，默认是 0，把它改成 1，保存。然后再打开首页 [http://localhost:8002/index](http://localhost:8002/index)，此时点击 `submit` 按钮，页面就会跳转到失败页面了（请看页面标题）。

不过目前 NEI 只支持以 `GET` 方式请求页面，其他方式暂时还不支持，希望 NEI 后续会补上这个功能。
