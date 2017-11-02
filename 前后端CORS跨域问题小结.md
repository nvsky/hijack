[TOC]


### 	CORS 跨域优势

> 1.兼容非跨域方案，也就是在同一个域名下ajax请求会自定降级普通请求，解决所有异步数据请求问题，这样比普通AJAX方式更加通用。

> 2.安全，开启认证信息或是允许所跨域的域，比JSONP安全。

> 3.目前在所有跨域方案中支持浏览器的范围是最广泛的，在从新封装了juqery ajax之后支持 ie8/ie9。

> 4.服务端容易支持，前后端没有任何技术成本。

### 配置方式

#### 前端：
**jquery ajax配置如下：**

```javascript

$.ajax({
    url: apiRootPath + "api/Account/Login",
    type: "post",
    data: {
        "UserName": userName,
        "Password": password
    },
    crossDomain: true, //jquery ajax需要配置说明是cors的请求。
    xhrFields: {
        withCredentials: true //在发送数据请求时，是否带上验证信息，即cookie。
    },
    dataType: "json",
    success: function (data) {
        if (data.State == true) {
            MLogin(userName, password);
        } else {
            $("#loginBtn").text("登录");
            $("#errorText").html(data.Message);
        }
    }
});

```

**qwest/fetch:**
>是很好支持cors，封装好了IE8/IE9支持，在内部已经实现了判断是否要cors协议。[qwest](https://github.com/pyrsmk/qwest)。

> 在默认配置里面增加 withCredentials: true  在发送请求时带上cookie 信息。

```javascript
const defaultOptions = {
  method: 'post',
  data: {},
  type: 'json',
  adapter, // resultDTO解析方法
  alertError: true, // 是否弹出错误提示窗口
  alertDenyAccess: true, // 是否弹出没有权限提示窗口
  parallel: false, // 是否并行发送批量请求
  withCredentials: true, //设置跨域请求Cookies
  isSuccess(xhr, resp) { // 自定义逻辑判断是否成功
    return resp.status === 'S' || resp.success === true || resp.status === 'success';
  },
  isAccessDeny(xhr, resp) { // 判断是否没有权限
    return resp.statusCode == '403' && resp.data;
  },
  getAuthUrl(xhr, resp) { // 获取授权url
    return APP_CONFIG.LOGIN;
  },
};
```

### 后端接口服务


#### 阶段一：OPTION

**Request Headers**
```javascript
Access-Control-Request-Headers:cache-control
Access-Control-Request-Method:POST
Connection:keep-alive
Host:billaudit.gooagoo.com
Origin:http://monitor.gooagoo.com
Referer:http://monitor.gooagoo.com/index/monitor.html
```
**Response Headers**
```javascript

Access-Control-Allow-Credentials:true
Access-Control-Allow-Headers:cache-control
Access-Control-Allow-Headers:x-requested-with
Access-Control-Allow-Origin:http://monitor.gooagoo.com
Allow:GET,HEAD,POST,OPTIONS
Access-Control-Max-Age:1728000

```

**说明：**

1. `Access-Control-Allow-Headers`如果浏览器请求包括Access-Control-Request-Headers字段，则Access-Control-Allow-Headers字段是必需的。它也是一个逗号分隔的字符串，表明服务器支持的所有头信息字段，不限于浏览器在"预检"中请求的字段。
2. `Access-Control-Request-Method`该字段是必须的，用来告诉服务端，用说明方法发送请求，上例中用POST方式发送请求。
3. `Origin`字段用来说明，本次请求来自哪个源（协议 + 域名 + 端口）,
服务器根据这个值，决定是否同意这次请求。`Access-Control-Allow-Origin:`保持严格一致。

**补充：**

1. `Access-Control-Expose-Headers` 
该字段可选。CORS请求时，XMLHttpRequest对象的getResponseHeader()方法只能拿到6个基本字段：Cache-Control、Content-Language、Content-Type、Expires、Last-Modified、Pragma。如果想拿到其他字段，就必须在Access-Control-Expose-Headers里面指定。上面的例子指定，getResponseHeader('FooBar')可以返回FooBar字段的值。

2. `Access-Control-Allow-Origin`当withCredentials = true; 允许请求带上验证信息即Cookies，设置Access-Control-Allow-Credentials = true的同时Access-Control-Allow-Origin的值不能为“*”，必须设置一个完整的域，只允许一条。这是浏览器CORS安全一种策略。

3. `Access-Control-Allow-Credentials`服务允许带上验证信息。

4. `Access-Control-Request-Headers`同第一点。
5. `Access-Control-Max-Age`用来指定本次预检请求的有效期，单位为秒。建议设置成7天有效时间（604800000），在此期间，不用发出另一条预检请求。

#### 阶段二：发送GET/POST请求
> OPTIONS请求是Cors的预请求，获取服务端对跨域请求所支持的http方法以及请求的配置和服务端验证是否允许此次请求。

**Request Headers**
> 正常的浏览器请求，以及带上验证信息。

```javascript
Cookie:cna=He1bDyx77jACAXkAHcFrtgQr; l=AkpKJgcXh3VlO/QVn2Lx6mBTGjrss85E; isg=Al9fYn-ydPGF7HDvCadEVjcu7rUHhbNmyyQsy_GsYY6EgH0C-ZTktyUYNKcE; _ga=GA1.2.70921764.1479294847; PASSPORT_VC=1B5VMFP3KE1NC8002OV0G23VIK0ML9UJ; com.gooagoo.passpart.sso.token.name=misUser1B5VMG2JJALF6H002OV0G23VIL0ML9UK
Host:billaudit.gooagoo.com
Origin:http://monitor.gooagoo.com
Referer:http://monitor.gooagoo.com/index/monitor.html
```

**Response Headers** 

```javascript
Access-Control-Allow-Credentials:true
Access-Control-Allow-Headers:cache-control
Access-Control-Allow-Headers:x-requested-with
Access-Control-Allow-Origin:http://monitor.gooagoo.com
Allow:GET,HEAD,POST,OPTIONS
```

#### 相关跨域文档
[Web 浏览器跨域通信解决方法-HTML5 message](https://git.gooagoo.com/hewenshan/doc/issues/8)

[前端跨域问题总结](https://git.gooagoo.com/hewenshan/doc/issues/9)
