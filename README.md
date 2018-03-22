# testQuickApp
初体验快应用

官方文档：https://doc.quickapp.cn/tutorial/getting-started/hello-world.html
官方论坛：http://bbs.quickapp.cn/index

## Step 1.搭建环境
#### 安装Nodejs

需要6.0以上版本，通过node -v可以查看当前版本，不会安装的参看安装教程  (注：不要用8.0版本！)

#### 安装hap-toolkit
执行如下命令:
  npm install -g hap-toolkit
  
安装完毕后执行hap -V（V 要大写）查看是否安装成功

## Step 2.新建工程
#### 创建工程项目
先cd到你的项目存放目录,执行项目初始化命令 ( yourProjectName 要替换成你的项目名 )
  hap init yourProjectName

#### 安装npm依赖
cd 到你新建的项目文件夹下，执行如下命令
  npm install
## Step 3.	编译项目
查看项目代码

找一个你自己趁手的IDE打开新建的项目即可（快应用暂时没有出官方的开发IDE）

简单介绍一下（可跳过）

src：项目源文件夹
src/manifest.json：项目配置文件
node_modules：项目的依赖类库
package.json：npm的项目配置文件

#### 编译项目

在你的项目文件夹下，执行如下命令
  npm run build	

【注意！】大部分第一次执行会遇到如下报错
Error: Cannot find module '/Users/***/***/node_modules/hap-tools/webpack.config.js'
莫慌，执行一次 hap update --force 即可解决, 再执行npm run build进行编译。

编译成功以后，工程项目会多处两个文件夹：
build：存放编译后的页面js文件和素材
dist：存放编译打包生成的rpk压缩文件，这个rpk就是快应用的最终执行文件了，提交市场就可以用它了(提交市场要release版本，后续再说)。

## Step 4.	真机预览
你的手机需要安装 快应用调试器 和 平台预览版 （下载后用ADB或者直接USB传输安装到手机。注意，两个apk都要安装哦！平台预览版是模拟快应用的运行时环境的。）
安装前面编译出来的rpk文件

#### 方法一： 本地安装预览

将你的工程中/dist目录下编译产出的rpk文件通过USB数据线或其他方式，复制到手机文件系统中。
打开手机上的“快应用调试器” 点击“本地安装” 选择手机文件系统前面复制进来的rpk文件，即可预览到你的快应用的界面。

#### 方法二： 扫码预览

在工程目录下执行如下命令启动本地服务(默认端口12306)
  npm run server
如果遇到端口冲突，可以执行npm run server -- --port 8080自定义端口号（8080可自定义）
服务启动后，会在终端显示本地服务地址和对应二维码

打开手机上的“快应用调试器”，点击“扫码安装”，扫这个二维码即可安装快应用进行预览。


如果遇到二维码扫码不成功，也可以点击右上角三个竖点的菜单按钮，选择“设置”，进入设置界面以后，将服务地址手动输入，然后返回主界面，点击在线更新即可进行安装预览。


如果提示安装失败，建议重新起一遍npm run server 重新来过。

> 原创作者：（只是记录下）
> 作者：大大花猫
> 链接：https://juejin.im/post/5ab27d8e518825557e78485e
