上一篇我们讲了如何通过不死鸟防封的会员中心免费生成泛域名证书，[点击链接查看上一篇文章](https://github.com/wechaturl/fangfeng-guide-articles/blob/master/ssl_manage_add_star_domain.mdcom/)，这篇文章主要如果通过文件认证方式生成证书。

#### 如果你有个域名xx.yourdomain.xx,想生成证书，但你可能没有dns管理权限，无法添加txt解析。那你不用担心，通过文件认证，即可生成证书，并且到期前会为你自动续期。

通过不死鸟防封生成的证书，你直接将公钥和私钥复制到你服务器配置好即可。如果你的域名用作于短网址，系统可在几秒钟内帮你部署到服务器。

1.免费注册成为不死鸟防封会员,github,google,邮箱均可注册

2.进入“业务管理-->证书+服务器-->https证书管理”

3.按照下图所示添加需要证书的域名

![image](https://static.cloudcdn.xyz/static/fangfeng-guide-articles/material/ssl_server/ssl_manage_add_file_domain.png)

4.点击开始生成即可(你需要先将域名别名解析到下面提示的地址)

![image](https://static.cloudcdn.xyz/static/fangfeng-guide-articles/material/ssl_server/ssl_manage_added_file_domain.png)

5.生成成功，你会获得公钥和私钥

![image](https://static.cloudcdn.xyz/static/fangfeng-guide-articles/material/ssl_server/ssl_manage_list.png)

######  欢迎你免费使用不死鸟防封，如果你觉得这篇文章帮助你了，请帮忙转发，谢谢！

本文作者:Adams

本文中文翻译:feri Dun

关于本文作者:曾就职于TX Europe,参与过TX核心业务,现供职于FB

