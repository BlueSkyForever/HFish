# HFish

HFish是一款安全、简单可信赖的跨平台蜜罐软件，允许商业和个人用户免费使用。

## 特点

+ 安全可靠：主打低中交互蜜罐，简单有效；

+ 蜜罐丰富：支持SSH、FTP、TFTP、MySQL、Redis、MySQL、Telnet、VNC、Gitlab、Exchange、Memcache、Elasticsearch、打印机、视像头、交换机、Wordpress、OA系统等20多种蜜罐服务，支持用户制作自定义Web蜜罐；

+ 开放透明：支持对接微步在线X社区API、五路syslog输出、支持邮件、钉钉、企业威胁、飞书、自定义WebHook告警输出；
+ + 快捷管理：支持单个安装包批量部署，支持批量修改端口和服务；

+ 跨平台：支持Linux x32/x64/ARM、Windows x32/x64平台；



## 链接

[官方网站](https://hfish.io/)：更多使用蜜罐、使用场景和玩法详见官网

[详细文档](https://hfish.io/docs/#/)：更详细的功能说明、故障排错指南



## 架构

HFish由控制端和节点端组成，控制端用来生成和管理节点端，并接收、分析和展示节点端回传的数据，节点端接受控制端的控制并负责构建蜜罐服务。



## 注意

+ Linux 安装无需root权限，但是会导致无法监听低于TCP/1024以下端口

+ 控制端使用 TCP/4433 和 TCP/4434 端口，节点端监听端口根据模拟的服务不同而不同

+ 节点端需要可访问控制端的 TCP/4434 端口，控制端不会主动访问节点端

+ 控制端默认用户名/密码：**`admin / HFish2021`**



## 部署控制端

先部署控制端，再通过控制端的Web页面配置节点端，安装包仅包含控制端和节点端，蜜罐服务包需要部署控制端后从 **`服务管理**` 页面联网下载或离线上传



可联网环境：如果用户的环境允许联网，建议使用以下快速部署步骤：

+ Linux x64 环境：
  + 在shell中运行命令：**`sh | curl https://hfish.io/install.sh`**
  + 请转到下面的配置段落继续阅读



\+ Windows x64 环境：

- 下载控制端安装包：从Github https://github.com/hacklcx/HFish/releases 或码云 https://gitee.com/lauix/HFish 下载最新安装包
- 解压缩后双击 **`server.exe`**
- 请转到下面的【配置控制端】段落继续阅读



离线部署：如果用户为隔离网络环境，请使用以下部署方式

+ Linux x64 环境：
  + 下载控制端安装包：从Github https://github.com/hacklcx/HFish/releases 或码云 https://gitee.com/lauix/HFish 下载最新安装包
  + 解压缩安装包：**`tar zxvf ./hfish-*-linux-*.tar.gz -C hfish`**
  + 进入安装目录：**`cd hfish`**
  + 启动控制端：**`nohup ./server &`**
  + 请转到下面的【配置控制端】段落继续阅读



## 配置控制端

新部署的控制端需要没有任何蜜罐服务，必须新增服务和节点，控制端和节点端可以部署在同一台机器上。



+ 新增服务
  + 浏览器中输入 **`https://`**，登录控制端
  + 进入 **`服务管理**` 页面
  + 如果当前控制端可联网，点击服务表格右侧的下载按钮，并等待服务下载完成
  + 如果当前控制端不可联网，点击右上角 **`新增服务`** 按钮，上传服务包，服务包下载地址： **`https://hfish.io/services.html`**



+ 新增节点
  + 浏览器中输入 **`https://`**，登录控制端
  + 进入 **`节点管理`** 页面，点击右上角新增节点按钮，根据节点操作系统和CPU架构动态创建安装包
  + Linux可以选择命令安装或下载节点程序运行，Windows只能选择下载节点程序运行



## 效果图

+ 攻击详情：记录所有对蜜罐的访问请求，包括正常请求、攻击行为、暴力破解

![image2021-6-7_13-57-19](http://img.threatbook.cn/hfish/20210611114902.png)



+ 扫描详情：记录对所有节点主机的UDP和SYN扫描

![image2021-6-7_17-18-11](http://img.threatbook.cn/hfish/20210611114934.png)

+ 蜜饵管理

![image2021-6-7_19-6-21](http://img.threatbook.cn/hfish/20210611115053.png)

+ 节点信息

![image2021-6-7_18-0-36](http://img.threatbook.cn/hfish/20210611115118.png)

+ 模板管理

![image2021-6-7_18-56-55](http://img.threatbook.cn/hfish/20210611115140.png)



+ 威胁情报对接

![image2021-6-7_19-0-11](http://img.threatbook.cn/hfish/20210611115158.png)

+ 告警配置

![image2021-6-7_19-4-10](http://img.threatbook.cn/hfish/20210611115224.png)

## 微信群

![HFish官方群的qr](http://img.threatbook.cn/hfish/20210611115258.png)