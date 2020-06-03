# qq微信域名防红防洪之使用https证书防劫持(泛域名证书免费生成)-不死鸟防封系列教程一

##### 不死鸟防封本着开放原则，具有完善的API接口，PHP SDK，JAVA SDK，有详细的api指导。你甚至可以拿着不死鸟防封开放程序 www.wechaturl.us 去免费并不受限制地搭建一个运营网站


```
本教程对应git教程
https://wechaturl.gitbook.io/wechaturl/https_ssl/ssl_add
```


>   在中国，众所周知的原因，TX会借助自己的产品链打击同行。比如大家最近2年2018年，2019年看到的腾讯和今日头条的垄断下的恶意封杀。

> 正如大家知道的，如果你开发了一个产品，但是这个产品和腾讯利益没有半毛钱关系。那你的产品设计之初，就应该充分预判TX未来可能会封你的业务。

##### 剖析腾讯系的产品如何劫持我们的非https网站内容。
1. 首先准备一个非https的网站
2. 开启web服务器log记录器
3. 在微信、qq、qq浏览器里面访问这个网址
4. 这时候你的服务器不仅能够看到你自己的ip地址访问的记录，并且还能够看到其他大型城市的idc机房的ip记录。
5. OK！你可能已经发现异常情况了。如果你还有兴趣，继续查看header，这时候你会发现这些idc机房的服务器修改了你的header，比如你的服务器只支持IPV4访问，但是通过header分析，居然支持ipv6访问
6. 继续！！你能否想起曾经非常流行的电信广告劫持，当然现在也非常流行。没错，这些idc机房用的劫持技术和电信广告劫持属于同一类技术
##### 为什么会出现这种情况？
###### 首先我们确定这个idc机房的ip是谁的？
> 毋庸置疑，腾讯计算机公司的。
##### 它为什么会这么去做？
- 云端大数据分析，
- 云端隐私分析
- 打击竞争对手
- 云端加速+大数据分析双用途
- 其他用途

### 有了以上的测试结果，是不是非常可怕？？！！

> 为了解决可怕的劫持行为，不死鸟防封推出了免费的https受信任证书生成，到期自动续期，并且支持泛域名证书生成。目前生成证书的数量没限制

1.免费注册成为不死鸟防封会员,github,google,邮箱均可注册

2.进入“**业务管理-->证书+服务器-->https证书管理**”

本文以它最复杂的生成的方式-==-泛域名证书==，讲解他是如何生成

> 官方也说了，为了避免用户操作出错，因此做了傻瓜化提示操作，你只需要按照他们的提示操作即可成功


---

1. 按照下图填写好，保存。域名切记要换成真实的域名（之所以泛域名生成较为复杂，原因是根域名和下一级域名都需要做dns解析）


![不死鸟防封-添加待生成证书的域名](https://static.cloudcdn.xyz/static/fangfeng-guide-articles/material/ssl_server/ssl_manage_add.png)


2.点击“点击开始”按钮

![image](https://static.cloudcdn.xyz/static/fangfeng-guide-articles/material/ssl_server/ssl_manage_added.png)

3.此时你会收到dns解析的内容

```
解析类型:TXT
-------------------------------
需解析域名1:_acme-challenge.yourdomain.com
记录值1:ggrj0oIaGnHQlSrJKbI7JUGR11qpL_wip3-wJRARuX4
-------------------------------
需解析域名2:_acme-challenge.youdomain.com
记录值2:KNqFfKj-FJqMY7_XepzlOkSMyDV_ouk2PUW2YW-7XW4
-----------因为你设置了“更多域名”，所以需要同时解析2个TXT记录-------------
生成日期:2020-05-25 22:51:34
重要说明(你刚刚解析后，请不要忙于继续，请先用命令行看看txt解析是否生效，生效一分钟后再点击记录[因为大多数dns公司有缓存功能]):
  1.为了使颁发证书成功率提高到98.9%，请一定要解析后再继续,如果恶意注册证书，我们不排除对你的户口禁用此功能；
  2.如果你没有域名管理权限，请改用 ‘文件验证’。
  3.1.通过nslookup命令行查看是否生效(或者dig)
  3.1.1.root@localhost:~$ nslookup -type=txt
                       > _acme-challenge.yourdomain


  3.2.通过dig命令行查看是否生效
  3.2.2.root@localhost:~$ dig  _acme-challenge.yourdomain txt

```


4. 解析完后，点击“继续”
5. 恭喜你！！生成成功
6. 你已经成功掌握了最复杂的生成证书的方法了
7. 将私钥和公钥拷贝到你的服务器上去配置即可

![image](https://static.cloudcdn.xyz/static/fangfeng-guide-articles/material/ssl_server/ssl_manage_list.png)


######  欢迎你免费使用不死鸟防封，如果你觉得这篇文章帮助你了，请帮忙转发，谢谢！

本文作者:Adams

本文中文翻译:feri Dun

关于本文作者:曾就职于TX Europe,参与过TX核心业务,现供职于FB
