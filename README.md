duke resume
======================

## 个人信息

**姓名**：曹德权

**性别**：男

**学校专业**：**西安欧亚学院**信息工程学院（软件专业）2006 – 2009

**微信**：18701471731

## 技术能力

> 带领团队协调推进工作，保证质量高效完成至极用户体验产品

> 有较强的分析问题与解决问题的能力，勇于接受新的挑战、有良好的代码习惯，结构清晰，命名规范，逻辑性强，代码冗余率低、耦合低

> 保证系统稳定、高效、健壮

* 8年B/S开发经验，具有Team管理经验
* 擅长：前端架构、爬虫、监控、数据可视化
* 精通：javascript、php、熟悉coffeescrip
* 掌握：AngularJS框架、熟悉backbone、react等框架，使用npm、gulp、webpack等构建工具集
* 熟悉：echarts、d3、bootstrap、phantom、casper、amazeUI、ANT DESIGN等相关组件库
* 掌握：项目管理和协同工具SVN、Git
* 使用api以JSON形式进行数据交互，完成相关业务逻辑编码


## 工作经历

### Front end director at gooagoo
---
2015 年 12 月 – 至今 (8 个月)前端技术部
gooagoo | 前端技术部
B2B | 规模:200+（人） 

#### 工作内容:

* 规划team季度OKR；
* 项目对接及推进、资源及工作协调分配；
* 使用gulp、webpack工具集做dev及production工程化；
* 使用angularjs、react做技术选型及项目构建；
* 推进测试及发布流程；

#### 项目构建:

+**移动端架构**:
+ +**架构A**：`node v6.1.0 (npm v3.8.6)  webpack ＋ amazeUI`

```javascript

    "构建"
    //browser-sync、del-cli、director、jquery、less、less-loader、postcss-loader、style-loader、css-loader、 autoprefixer、file-loader、image-webpack-loader、html-webpack-loader、extract-text-webpack-plugin、webpack、webpack-dev-middleware、webpack-hot-middleware、copy-webpack-plugin等
    
    "组件" amazeui v2.7
    
    "服务" npm run start 
    //{scripts : { start : browserSync.create().init({server:{baseDir:[], middleware:[]}}) }};
    
    "生产" npm run build
    //{scripts : { build : webpack --config webpack.config.js }};
    //webpack.config.js : module.exports = {entry : [], output : {}, module : {loaders : [ test : /rule/, loaders : [], include : [] ]}, plugins : [] }

''
```
- +**架构B**：`node v0.12.2 (npm v2.7.4) gulp v3.9.0  gulp + amazeUI`

```javascript

    "构建"
    //browser-sync、run-sequence、del、director、jquery、gulp、gulp-load-plugins、gulp-less、gulp-csso、 gulp-autoprefixer、gulp-imagemin、gulp-size、gulp-htmlmin、gulp-uglify、gulp-rename、gulp-replace、watchify等
    
    "组件" amazeui v2.5
    
    "服务、生产" gulp serve    
    task : gulp.task(task, function(){return gulp.src([]).pipe()});
    runTask : gulp.task(runTask, function(){ runSequence(‘clean’, [taskNams], ‘watch’) };
    runServe : gulp.task('serve', ['runTask'], function() { browserSync({ server : ‘dist’ }); gulp.watch(['dist/**/*'], browserSync.reload); });

''
```

-**PC端架构**：
- +**架构A**：`node v0.12.2 (npm v2.7.4) gulp v3.9.0  gulp + angularjs ＋ material-design template ＋ webpack`

```javascript

    "构建"
    //browser-sync、run-sequence、del、jquery、gulp、gulp-load-plugins、watchify等（起服务）
    //css-loader、less、less-loader、style-loader、file-loader、url-loader、extract-text-webpack-plugin、webpack、webpack-dev-middleware、webpack-hot-middleware、copy-webpack-plugin等（打生产包）
    
    "组件" angularjs ＋ material-design template
    
    "服务" gulp serve
    gulp.task('serve', ['taskNames'], () => {
        browserSync({
            notify: false,
            server: ['angularjs'],
            port: 3000
        });
        gulp.watch(['angularjs/*'], browserSync.reload);
    });
    
    "生产" npm run build
    //{scripts : { build : webpack --config webpack.config.js }};
    //webpack.config.js : module.exports = {entry : [], output : {}, module : {loaders : [ test : /rule/, loaders : [], include : [] ]}, plugins : [] }

''
```


**系统环境**：MAC OS；

**开发工具**：sublime；

**框架及组件**：angular、react、redux、amazeui、bootstrap、ant.design、babel等；

**开发语言**：JavaScript、es6、html、css；

<br/>
###资深前端 at fuyoukache.com
---
2015 年 4 月 – 2015 年 12 月 (9 个月)中国 北京市区
fuyoukache | 研发部 | 资深前端、Tech Lead
物流O2O | 合资 | 规模:300+（人） 

#### 工作内容：
* 团队任务对接、工作协调分配；
* Github管理code review；
* 使用gulp、web starter kit做项目构建；
* 系统交互、业务逻辑的完成；
* 生产环境的打包、发布；

#### 个人完成项目：
- [微信经纪人web app]
 + 开发周期：2015-04-30/2015-05-15（2w）;
 + 运行环境：微信、WebView APP（各安卓市场可下载：福佑卡车经纪人端）；
 + 项目构建：使用Amaze UI web starter kit版以单应用形式构建web app项目；
 + 项目打包：使用gulp为项目做工程化编译合并压缩打包；
 + 项目质量：首次加载<550k，应用内部切换加载+-15k，确保项目稳定、健壮、高效；

- [fuyoukache.com]
 + 开发周期：2015-06-23/2015-07-14（3w）;
 + 运行环境：PC为主、多端为辅；
 + 项目构建：使用web starter kit做构建、以bower做资源管理，引入bootstrap、bootstrap-table、autoregion、daterangepicker、jquery-validation、select2、bootstrap-star-rating等组件库，使用import做资源加载、js 做兼容加载；
 + 项目打包：使用gulp为项目做工程化合并压缩打包，replace做资源调整；
 + 项目质量：首次加载+-2.4M，切换加载按内容资源情况轮；

- [微信问答 web app：http://123.56.112.151/wl/]
 + 开发周期：2015-07-23/2015-07-25（2d）;
 + 运行环境：微信、移动端浏览器；
 + 项目构建：使用Amaze UI web starter kit版以单应用形式构建web app项目；
 + 项目打包：使用gulp为项目做工程化编译合并压缩打包；
 + 项目质量：确保项目稳定、健壮、高效；

- [全新途胜答题闯关游戏 web app：http://123.56.112.151/dist-tusheng/]
 + [Github source：https://github.com/nvsky/game-tusheng]
 + 开发周期：2015-08-24/2015-09-03（11d）;
 + 运行环境：微信、移动端浏览器；
 + 项目构建：使用Amaze UI web starter kit版以单应用形式构建web app项目；
 + 项目打包：使用gulp为项目做工程化编译合并压缩打包；
 + 项目质量：确保项目稳定、健壮、高效；


#### 团队项目：
- 一起维护fuyoukache.com、微信经纪人web app；


**系统环境**：Ubuntu、MAC OS、Nginx；

**开发工具**：sublime、webstorm、sourcetree；

**框架使用**：amazui、bootstrap等；

**开发语言**：JavaScript、html、css；

<br/>
### JavaScript Developer And Web TL at kaikeba
---
2013 年 9 月 – 2015 年 4 月 (1 年 8 个月)中国 北京市区
kaikeba | 研发部 | 数据平台高级工程师（前端架构、数据可视化）
计算机 | 合资 | 规模:200+（人） 

#### 工作内容：
* 开发文档、需求设计、业务逻辑文档编写；
* 代码编写；
* 封装搭建健壮、稳定、高效、响应式前端框架；
* 结合yeoman bower grunt工具进行项目构建及发布；
* 使用backbone、bootstrap进行快速迭代开发；
* phantom casper对数据进行整理订阅；

#### 个人完成项目：
* 离线MAP全球网点监控：(https://github.com/nvsky/map_off_line) 基于google地图的瓦片，通过核心算法：M坐标、屏幕坐标、经纬度坐标相互转换实现瓦片加载、zoom层级切换、拖拽、鼠标效果等；结合d3绘制地图区域界线、标注、动态连线等，监控以展现全球业务网点的事件响应；

* DashBoard：此项目使用bootstrap＋echarts快速迭代开发、结合yeoman bower grunt完成自动化部署，使用php完成接口代理及用户认证；

#### 团队项目：
* Jupiter管理系统：此项目参与部分模块（用户权限、用户角色、场景配置、日志、模型管理等模块）的业务逻辑的编写及维护，此框架中用到的tree、grid、ComboBox均适用ligerui插件；


**系统环境**：Ubuntu、MAC OS、Nginx；

**开发工具**：webstorm、sublime、aptana、sourcetree；

**框架使用**：backbone、bootstrap、echarts；

**开发语言**：JavaScript、coffeescript、PHP、html、css；

**日常工作**：封装框架，接口、模型定义，业务逻辑实现，数据整理订阅；

<br/>
### javascript工程师 at 易视腾
---
2012 年 7 月 – 2013 年 9 月 (1 年 3 个月)中国 北京市区
北京易视腾科技有限公司 | 研发部 | JS高级工程师/TeamLead
计算机硬件及设备 | 合资 | 规模:100-499人 

#### 工作内容：
* 负责终端JavaScript编码工作（框架开发：接口、模型、控制层业务逻辑）； 
* 负责不同电视盒子终端（三星SmartTV、央视CNTV、三零、Ccbox）的代码移植整合；
* 协调团队工作；

#### 个人完成项目：
* 南京有线：南京有线电视盒子的定制模块（品牌专区），此项目前段JS框架为纯JavaScript脚本语言编写。此框架整体设计流程包括：接口、模型的定义，控制层业务逻辑，视图展现；遵循传统MVC框架设计模式；

* 通联支付：此项目前端JS代码功能实现部分包含model、contrl、interface等模块；

#### 团队项目经验：
* CIBN EPG2.0：此项目参与盒子整体5个专区（用户中心、视听专区、品牌专区、应用专区、系统设置）的业务逻辑的编写维护；

* 不同平台的版本整合：CCBox、央视CNTV（此盒子应用专区增加android应用的安装、卸载、排序、运行等功能）、三星SmartTV（此版chrome浏览器webkit核心不支持CSS3效果，其中引入jQuery库）、三零凯天；

**系统环境**：Linux、Apache、php、mysql；

**开发工具**：Aptana、SSH（Secure Shell）、AndroidSDK；

**框架使用**：Team内部框架；

**开发语言**：JavaScript；

**日常工作**：框架开发，接口、模型定义，控制业务逻辑实现，不同盒子的终端移植，BUG修复

<br/>
### PHP高级工程师 at 国富安
---
2009 年 2 月 – 2012 年 7 月 (3 年 6 个月)中国 北京市区
北京国富安电子商务安全认证有限公司 | 研发部 | PHP工程师
计算机硬件及设备 | 国企 | 规模:100-499人 

#### 工作内容：
* 负责写项目WebUI开发文档、并根据需求与开发文档设计WebUI效果图；
* 负责选定及调整WebUI的框架，用过的js框架有：Extjs、jQuery.LigerUI；
* 负责PHP代码编写工作；
* 写相关项目Web部分软件说明文档；
* 完成相关技术调研、攻坚等；.

#### 项目经验：
* VPN iPass3000：WebUI 参与编码工作（采用socket数据通讯方式）；

* LoadPass负载均衡：客户端的编码及业务逻辑实现（PHP脚本）工作（socket通讯方式，独立完成项目）
；
* vPass虚拟化云平台接入：参与管理端WebUI开发（php+mysql+socket）、客户端WebUI开发（php+mysql）；


**系统环境**：Linux、Apache、Nginx、php、mysql；

**开发工具**：EclipsePHP Studio、Dreamweaver CS3、SSH（Secure Shell）、Fireworks CS4；

**框架使用**：ThinkPHP、Smarty、Ext js、jQuery.LigerUI、jpGraph；

**开发语言**：PHP、JavaScript/jQuery；

**日常工作**：完成开发文档、PHP编码及业务逻辑、写软件说明文档（带项目）、出WebUI效果图、相关技术调研、攻坚等；

### End