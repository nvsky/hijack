# CNPM私有化部署和使用
[TOC]

## 域名申请
	
	npm.gag.cn
	
> **注：** 默认到7001端口，7002端口也开通。
 
## 安装环境依赖

1. [Node](https://nodejs.org/en/)

2. [GIT](http://www.liaoxuefeng.com/)

3. NPM(node已经包含)

4. [CNPM](https://npm.taobao.org/)

5. MySQL

6. [cnpmjs.org](https://github.com/cnpm/cnpmjs.org)客户端包


## 安装步骤

_1. 下载CNPM包：https://github.com/cnpm/cnpmjs.org.git

_2.  在目录下运行 npm install 安装所有依赖

_3.  创建Mysql数据库，本地数据库用户名：root，密码：root，使用cnpm 提供的数据库脚本db.sql

```
mysql -uroot -proot -e 'DROP DATABASE IF EXISTS cnpmjs_gag;'

mysql -uroot -proot -e 'CREATE DATABASE cnpmjs_gag;'

mysql -uroot -proot 'cnpmjs_gag' < /Users/hou/work/cnpm_org/docs/db.sql(db.sql地址)

mysql -uroot -proot 'cnpmjs_gag' -e 'show tables;'

```

_4.  修改配置/config/index.js文件

```
	database:{
     db: ‘cnpmjs_gag’,
     username:’root’,
     dialect:’mysql’
	}
	...
	
	enablePrivate: true, // enable private mode 
	admins: { admin: 'fe@gooagoo.com', }, 
	...
	
	注释bindingHost一行，对外网开放。
	//bindingHost: '127.0.0.1', 
	// only binding on 127.0.0.1 for local access
	
	...

	scopes:['@gag','@cnpm','@npm'],
	
```

_5. 运行 npm run start

_6.  检查运行
```
curl http://localhost:7001   //这是提registry 发布和安装
curl http://localhost:7002  //这是网页访问的端口
```
## GOOAGOO通用的Gighub、NPM 账号

```

GitHub:   fe@gooagoo.com gooagooF2e/gooagoo@f2e
NPM:   fe@gooagoo.com f2e/gooagoo@f2e


```


## npm 混合公共仓库和私有仓库

_1. 配置npm 和 cnmp 混合

> 我们除了使用自己的私有库，还可以使用淘宝的NPM库，这样可以有效地避免国内访问国外NPM库，网络不通的问题。


> 按照上面的方法，把registry配置为https://registry.npm.taobao.org 就行了。
> 如果cnpm的镜像里没有需要的包，cnpm会在30分钟左右时间把npm包同步到cnpm镜像，再次安装即可。还有一个方法直接在https://npm.taobao.org/sync/connect#logid=2659132进行手动同步，需要15分钟同步时间。


```
 npm login //登陆自己的NPM地址

 npm set config --registry http://registry.npm.taobao.org
```

```
~  vi ~/.npmrc

registry = "https://registry.npm.taobao.org/"

```

_2. 配置cnpm的scope为 @gag


> npm.gag.cn 的通用账号为 

Username: f2e

Password:gooagoo@f2e

Mail:fe@gooagoo.com

```
npm login --registry http://npm.gag.cn:7001 --scope=@gag

npm login --registry http://npm.gag.cn:7001 --scope=@gag --userconfig=$HOME/.cnpmrc
```

_3. 安装私有仓库

```
npm install @gag/test
```

## 私有包发布

_1.  配置package.json
 
```
{
  "name": "@gag/helloworld",
  "version": "1.0.0",
  "description": "my first scoped package",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}
```
_2.  包发布

> 不会发布到cnpm以及公网。

> npm.gag.cn 的通用账号为 

Username: f2e

Password:gooagoo@f2e

Mail:fe@gooagoo.com


> 添加发布源

```
npm adduser --registry=http://npm.gag.cn:7001 --scope=@gag

//Username: f2e

//Password: gooagoo@f2e

//Email: (this IS public) fe@gooagoo.com

```


> 登陆|发布

```
npm login --registry=http://npm.gag.cn:7001 --scope=@gag

//Username: f2e
//Password:gooagoo@f2e
//Mail:fe@gooagoo.com

> helloworld/
npm publish
```

> 全部带上对应的端口号

## 参考文献

[npm 混合公共仓库和私有仓库](https://breeswish.org/blog/2016/02/16/npm-hybridize-public-and-private-repository/)

[MacPro 使用cnpmjs搭建私有npm服务](http://www.cnblogs.com/wyzfzu/p/4149310.html)

[使用cnpm搭建企业内部私有NPM仓库](https://segmentfault.com/a/1190000000368906)

[CNPM搭建私有的NPM服务](http://blog.fens.me/nodejs-cnpm-npm/)

[cnpm.org issue](https://github.com/cnpm/cnpmjs.org/issues)

[如何混合使用npm的公共仓库和cnpm搭建的私有仓库](https://github.com/cnpm/cnpmjs.org/issues/929)
