# 颜值测试小程序

使用小程序云函数和百度云的 ai 接口做的一个颜值测试小程序。

##### 体验

![小程序码](https://pcdn.wxiou.cn//20200826191041.jpg)

## 实现过程

使用 `wx.chooseImage` 选择图片，使用 `wx.cloud.uploadFile` 上传图片并获取到图片的 `fileID`，传给自己写的云函数`getImageData`。

云函数中使用 `cloud.getTempFileURL` 获取到图片 https 协议的临时路径，把图片路径传给百度云接口，获取到信息后返回给前端。


## 更新日志

#### v0.1
* 2020-06-07 完成基本的功能开发

#### v0.2
* 2020-08-26 修改第一版中AK以及SK暴露在代码中引起的安全问题，修改为云环境端变量，进行传参
* 2020-08-26 修改第一版中用户上传的图片保存的问题，第一版用户上传的图片会保存在云开发的大小为5G的云存储中，用户量大的时候可能容量不够，也会因为存储用户数据而引起不必要的麻烦


## 安装过程
#### 1、下载源码，并开通百度智能云API
- [百度智能云](https://cloud.baidu.com/)

注册百度智能云账号，选择人脸识别，新建一个应用
![](https://pcdn.wxiou.cn//20200826132425.png)


这里的AK以及SK待会要用
![](https://pcdn.wxiou.cn//20200826132625.png)

#### 2、新建小程序，选择云开发
新建一个目录，新建一个云开发项目，然后它会初始化目录结构，初始化目录后，把下载的源码和新建的项目进行替换，因为直接导入的话没有用
![](https://pcdn.wxiou.cn//20200826133230.png)

#### 3、修改配置
点击云开发，新建一个环境，名称随意
![](https://pcdn.wxiou.cn//20200826133545.png)

新建以后可以得到云环境id
![](https://pcdn.wxiou.cn//20200826133657.png)

填入`app.js`文件以及云函数`getImageData`的`index.js`文件的配置里面
![](https://pcdn.wxiou.cn//20200826133817.png)
![](https://pcdn.wxiou.cn//20200826133912.png)

点击云数据库，新建一个名为`files`的集合

![](https://pcdn.wxiou.cn//20200826134058.png)


检查当前是否连接了云开发环境
![](https://pcdn.wxiou.cn//20200826134316.png)

选择云函数目录，右键 选择`上传并部署：云端安装依赖`，`getImageData`以及`getTheme`都需要部署一次

来到云开发环境，可以看到部署的云函数，点击版本管理
![](https://pcdn.wxiou.cn//20200826134941.png)

点击配置
![](https://pcdn.wxiou.cn//20200826135021.png)

添加两个环境变量
* clintId : 第一步的百度云API的AK
* clientSecret : 第一步的百度云API的SK
![](https://pcdn.wxiou.cn//20200826135148.png)


调试小程序，以上步骤没问题，便可正常运行

如有问题，请提issues

## 关于广告

目前的版本都写了广告，用户上传图片后点击测试会触发激励广告，考虑刚开始接触小程序可能开通不了广告，注释下面代码即可关闭广告，可接通广告时把注释取消填入相关ID即可
![](https://pcdn.wxiou.cn//20200826141123.png)



## 参考文档

- [云开发文档](https://developers.weixin.qq.com/miniprogram/dev/wxcloud/basis/getting-started.html)
- [百度云人脸检测接口文档](http://ai.baidu.com/docs#/Face-Detect-V3/top)

### 喜欢项目的请给个Star, 谢谢了！
