---
title: "aab包测试方法"
date: 2022-04-11T01:33:50.271Z
draft: false
---

## 前言

&emsp;&emsp;由于现在Google提审包体只能使用aab包体，不再使用apk包体，当我们想进行测试的时候将aab扔进手机内时无法直接安装的，是需要将aab转为成apks包体，然后使用命令行给手机进行安装才可以的，故今天来记录一下如何进行测试。

## 方法说明

### MAC

1. 首先需要安装bundletool

`brew install bundletool`

2. 将aab转成apks

`bundletool build-apks --bundle=AAB文件名称.aab --output=APKS文件名称.apks --ks=密匙文件名.jks --ks-pass=pass:密匙文件密码 --ks-key-alias=密匙名 --key-pass=pass:密匙密码`

若无jks则使用

`bundletool build-apks --bunlde=AAB文件名称.aab --output=./APKS文件名称.apks`

3. 安装apks (*需要使用USB将手机连接到电脑)

`bundletool install-apks --apks=APKS文件名称.apks`

### WINDOW

1. 首先需要下载bundletool.jar文件

[https://github.com/google/bundletool/releases](https://links.jianshu.com/go?to=https%3A%2F%2Fgithub.com%2Fgoogle%2Fbundletool%2Freleases)

2. 将aab转成apks

`java -jar bundletool文件名.jar build-apks --bundle=AAB文件名称.aab --output=APKS文件名称.apks --ks=密匙文件名.jks --ks-pass=pass:密匙文件密码 --ks-key-alias=密匙名 --key-pass=pass:密匙密码`

3. 安装apks  (*需要使用USB将手机连接到电脑)

`java -jar bundletool文件名.jar install-apks --apks=APKS文件名称.apks`

## 总结

&emsp;&emsp;以上即为aab测试的方法，虽然目前都是先构建apk进行测试，然后测试完毕后直接构建aab进行交付，按理来说应该不会有什么问题出现，偶尔还是将aab通过安装在手机上进行测试测试比较保险，那今天内容就到这里结束了！

&emsp;最后的最后，一碗鸡汤奉上，Sweat is the lubricant of success。

