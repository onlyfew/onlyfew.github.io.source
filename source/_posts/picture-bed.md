---
title: 使用PicGo和七牛云搞定免费图床
date: 2020-02-05 08:18:40
tags: [技术, PicGo, 图床, 七牛云, 工具, 免费, 器]
categories: 技术
---

## 一、简介
永澄老师在[搞定一个图床](http://kt.runwith.cc/yryc/4-recommendation/picstore)中选用的是收费版的阿里云OSS和iPic工具，此两者均为收费工具，土豪随意，我探索了基于七牛云免费额度和PicGo开源工具的免费方案。
七牛云免费额度如下，一般情况下够用了：
![](http://image.onlyfew.cn/bitcron/20200205140329.png)

<!-- more -->

## 二、配置方法
### 2.1 七牛云配置过程
1. 注册账号
2. 个人账号需认证身份，约1小时内即可认证通过
3. 进入对象存储管理页面，如下图
    ![](http://image.onlyfew.cn/bitcron/20200205140630.png)
1. 新建空间，上图中已经有我之前创建的一个空间
    ![](http://image.onlyfew.cn/bitcron/20200205141117.png)
1. 进入空间概览页面，获取CDN测试域名备用
    ![](http://image.onlyfew.cn/bitcron/20200205143107.png)
3. 进入个人中心-密钥管理界面，获取到AK和SK备用
    ![](http://image.onlyfew.cn/bitcron/20200205142757.png)

### 2.2 PicGo配置过程
1. 访问[PicGo官网](https://molunerfinn.com/PicGo/)可链接到[下载PicGo页面](https://github.com/Molunerfinn/picgo/releases)，下载并安装
2. 进入设置页面，选择七牛云图床
![](http://image.onlyfew.cn/bitcron/20200205143350.png)
>  - AK和SK填写上面密钥管理中获取到的内容
>  - 空间名填写上面创建空间的空间名
>  - 访问网址为上面的CDN测试域名
>  - 存储区域：华东为z0，华北为z1
>  - 网址后缀可选
>  - 存储路径可根据情况设置，会变成图片的一级文件夹

## 三、图床使用
支持拖拽上传、快捷键上传剪贴板图片等功能，非常易用，具体可参见[PicGo官网](https://molunerfinn.com/PicGo/)

## 四、参考资料
- 易仁永澄老师写的[搞定一个图床](http://kt.runwith.cc/yryc/4-recommendation/picstore)，整个专题都值得一看
- [如何用七牛和picGO设置免费图床](https://www.jianshu.com/p/0997d0d15e55)
- 七牛存储区域列表
    ![](http://image.onlyfew.cn/bitcron/20200205144615.png)
