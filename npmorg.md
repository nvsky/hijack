# 发布npm包

## 1、创建npm账号

- 注册一个npm账号
- 命令行工具添加账号(npm adduser)
```
$ npm adduser   
Username: your name
Password: your password
Email: yourmail[@gmail](/user/gmail).com
```

## 2、创建一个node的模块

- npm init (注意创建模块前，先去npm官网确认模块名是否未被占用)
```
name: (npm-demo) npm-demo-navy
version: (1.0.0) 0.0.0
description: npm test
entry point: (index.js) 
test command: make test
git repository: https://github.com/navyxie/bankcardinfo
keywords: npm test demo
author: navyxie
license: (ISC) 
```
```
lib目录下存放业务逻辑文件
test目录下存放单元测试用例
.npmignore记录哪些文件不需要被发布到npmjs.org
.travis.yml是持续集成服务travis的描述文件
index.js是入口文件
makefile方便我们用make test进行测试
README.md是此module的描述和使用方法
```
- 编写代码
```
index.js(module.exports = require('./lib/test');)
lib/test.js(module.exports = function(){return 'ok';})
test/
```

## 3、发布npm包
- 1.npm publish . (基于当前目录进行发布)

```
npm info it worked if it ends with ok
npm info using npm@1.4.28
npm info using node@v0.10.35
npm info prepublish npm-demo-navy@0.0.0
npm info trying registry request attempt 1 at 10:53:53
npm http PUT https://registry.npmjs.org/npm-demo-navy
npm http 200 https://registry.npmjs.org/npm-demo-navy
+ npm-demo-navy@0.0.0
npm info publish npm-demo-navy@0.0.0
npm info postpublish npm-demo-navy@0.0.0
npm info ok 
```

## 4、测试使用npm包

```
var demo = require("npm-demo-navy");
console.log(demo());
```

## 5、对npm包进行管理（tag）
- npm tag npm-demo-navy@0.0.2 0.0.2 (npm publish npm-demo-navy --tag 0.0.2，添加新文件时继续执行相同的tag版本)
- npm info npm-demo-navy (查看包信息)
```
{ name: 'npm-demo-navy',
  description: 'npm test',
  'dist-tags': 
   { latest: '0.0.2',
     'tag_0.0.2': '0.0.2',
     'tag_0.0.3': '0.0.3' },
  versions: [ '0.0.0', '0.0.1', '0.0.2' ],
  maintainers: 'navyxie <navyxie2010@gmail.com>'
}
```
- npm tag npm-demo-navy@0.0.3(version) latest (更新版本)
- npm publish --tag tag_0.0.9 (发布version & tag),已发布的tag不能再修改发布

## 6、npm其他使用(scripts)

- 跑测试
- 执行脚本命令
- 安装，预安装，卸载等
- 代码提交（git）
- 项目构建
- ...

## 7、全局模块安装
以grunt为例：

- which grunt (/usr/local/bin/grunt)
- cd /usr/local/bin/
- ll  (lrwxr-xr-x  1 root  admin        39 11 26 11:26 grunt -> ../lib/node_modules/grunt-cli/bin/grunt) ,实际上是创建软链
- /user/local/lib/node_modules/grunt


## 8、更改全部模块路径

- 更改全局包的安装路径（推荐）

  1 在你想要存放全局的包的路径下创建文件夹（mkdir ~/.npm-global）

  2 设置新的全局文件路径（npm config set prefix ‘~/.npm-global’）
  
  3 更改profile文件,添加以下代码, 因为此方法导致一个问题，cli命令全局安装的时候不能运行，所以我们要添加一下路径（export PATH=~/npm-global/bin:/home/cur_user/.npm-global/bin:$PATH）
  
  4 更新系统变量（source ~/.profile）
 ```
 详情请看 https://docs.npmjs.com/getting-started/fixing-npm-permissions
 ```

- 更改全局包的安装路径的权限（不推荐）
 1 找到npm 的文件夹（npm config get prefix）
 2 将文件夹拥有者改为你自己（sudo chown -R `whoami` <directory>）


## npm离线安装的解决方案

1 Registry 代理

 - npm-proxy-cache(npm --proxy http://localhost:8080 --https-proxy http://localhost:8080 --strict-ssl false install)
 - local-npm(npm set registry http://127.0.0.1:5080)
 - npm-lazy(npm --registry http://localhost:8080/ install socket.io)

2 npm-cache install替代

 - npm-cache install

3 node_modules作为缓存目录

 - [Freight](https://github.com/node-freight/freight)
 - [npmbox](https://github.com/arei/npmbox)

 ## 参考
- https://github.com/npm/npm
- https://www.npmjs.org/doc/api/npm-publish.html
- https://www.npmjs.org/doc/cli/npm-adduser.html
- http://docs.travis-ci.com/user/languages/javascript-with-nodejs/
- http://docs.travis-ci.com/user/database-setup/
- http://semver.org/
