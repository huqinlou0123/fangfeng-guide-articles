#### 不死鸟的短网址域名系统完全支持防劫持ip库拦截,但是一定要搭配https安全链接才会发挥最大的效果
经过开源团队长期跟踪,发现以下大厂存在劫持,

- 鹅厂(尤其是http劫持非常严重,不断重复劫持访问,加重服务器的负担)
- 360厂(不断重复劫持访问,加重服务器的负担)
-  HW(拼音首字母)
- 其他小厂

以上厂商还存在TLS+HSTS劫持

这篇文章,我们重点介绍先自己的短网址配置https访问+HSTS防劫持+防劫持ip库拦截.

<font color=red size=3>本功能是不死鸟防红防封免费提供的</font>

### 首先,你需要准备以下东西:
1.一台全新的centos  7.* 64位+不要求性能的云服务器.免费为你配置SslManager软件
```
    如果你觉得不方便提供,可以使用不死鸟微信防红防封系统的服务器

```
2.一个域名



### 接下来

1. 免费注册成为不死鸟防封会员,github,google,邮箱均可快速注册

2. 进入"业务管理-->入口域名池--> 短网址域名列表"  ,点击添加短网址域名,按照如下图设置即可.

![image](https://static.cloudcdn.xyz/static/fangfeng-guide-articles/material/ssl_server/ssl_manage_short_domain_add.png)

```
    请注意,前面一定要选择https://
    证书来源:系统自动部署:我公司会为你免费生成证书;本人已经部署:你自己已经把证书部署好了
    当你保存后,会有文字提示,按照提示操作
```
3. 进入"业务管理-->证书+服务器--> https证书管理",找到对应的域名,点击"点击开始",稍等10多秒后,即为你颁发受任何浏览器信任的证书.如下图所示.

![image](https://static.cloudcdn.xyz/static/fangfeng-guide-articles/material/ssl_server/ssl_manage_added_file_domain.png)

```
    如果这里没有找到对应的域名,那就手动添加一个待生成证书的域名
```

3.回到"业务管理-->入口域名池--> 短网址域名列表",点击"https部署"

![image](https://static.cloudcdn.xyz/static/fangfeng-guide-articles/material/ssl_server/ssl_manage_synchronous_management.png)

|  关键词   | 说明  |   其他  |
|  ----  | ----  | ----  |
| 同步的伺服器  | 待同步的服务器 | 如果是系统服务器,系统会定时为你同步,或者联系帮你手工同步;当然你自己的服务器就可以随时操作实时同步 |
| 签发域名  | 域名 | 无 |
| 证书指纹  | 证书全球唯一标识 | 不死鸟防封是通过指纹管理不同证书的 |
| id messag_id  | id:是同步记录 | messag_id:本次同步日志,当遇到错误,这里能分析问题 |



```
    1.系统通过UDP加密协议将证书传递到你的伺服器，然后进行自动化配置
    2.同步成功后，你可以通过https访问这个域名，如果浏览器不爆红，说明成功
```

4. 进入"业务管理-->证书+服务器--> https证书同步",你能看到这个证书的同步记录.由于本次演示时候,使用的是系统服务器,系统服务器默认配置了"强制https"和 "防HSTS攻击",如果你需要这2个功能,你可以取消打钩.本文章底部有对这2个功能的单独介绍

![image](https://static.cloudcdn.xyz/static/fangfeng-guide-articles/material/ssl_server/ssl_synchronous_record.png)

5. 同步成功后,回到"业务管理-->入口域名池--> 短网址域名列表",点击"https部署".此时看到"同步成功",说明成功了.在的右边,你能看到"https到期"的时间

6. 好了,域名已经成功配置了防qq微信劫持ip库劫持+https证书

7. 如何测试是不是防止了微信劫持?下一章节详细解说.

### 强制https
1.如果是http访问,则强制301到https
2.此方法是我们对web服务器强制设置https，而非程序逻辑控制301

### 防HSTS攻击

1.如果是http访问,则强制301到https

2.此方法是我们对web服务器强制设置https，而非程序逻辑控制301

### 谁在使用HSTS进行攻击
1.云加速服务商

2.不信任的政府机构

3.黑客
### 如何知道我的域名是否加了HSTS
1.浏览器访问https网站

2.然后打开"chrome://net-internals/#hsts"

3.检索"Query HSTS/PKP domain"

4.搜索你访问的域名，你将会得到以下内容(如果检索不到，说明没有开启hsts)

```
Found:
static_sts_domain:
static_upgrade_mode: UNKNOWN
static_sts_include_subdomains:
static_sts_observed:
static_pkp_domain:
static_pkp_include_subdomains:
static_pkp_observed:
static_spki_hashes:
dynamic_sts_domain: www.yourdomain.com
dynamic_upgrade_mode: FORCE_HTTPS
dynamic_sts_include_subdomains: true
dynamic_sts_observed: 1589614655.055429
dynamic_sts_expiry: 1590046655.055423
```

##  欢迎你免费使用不死鸟防封，如果你觉得这篇文章帮助你了，请帮忙转发，谢谢！

本文作者:Adams

本文中文翻译:feri Dun

关于本文作者:曾就职于TX Europe,参与过TX核心业务,现供职于FB