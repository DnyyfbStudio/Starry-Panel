# Starry-Panel
一个简易的多功能Oauth平台<br>
## 环境要求
以下为必须条件：<br>
- PHP 7.1
- MySQL 5.6.50
- phpMyAdmin 4.4
- - -
以下为可选条件：<br>
- Nginx 1.16.1
## 安装
将压缩包中的所有文件解压至网站根目录。然后访问网站，确保能看到登录界面。<br>
将压缩包中随附的“import.sql”使用 phpMyAdmin 导入数据库。<br>
进入网站目录，修改各个文件内的缺省值。不理解的参数请开 issue 或 QQ 2381358065询问。<br>
再次登录网站，使用“注册”链接注册一个账号，确保能正常注册和登录。
## 一些要求
在各个界面右下角的“Starry Panel vx.x | 电脑菌工作室 倾注代码”不要去除。<br>
其余的内容和代码可自行随意修改。
## 需要注意
本平台传递的所有数据和 Cookie 均未加密，容易发生安全问题。您可自行编写加密逻辑。<br>
只是一个电脑菌的php初次试水项目，问题之处还请指正，轻喷
## 示例页面
[http://110.42.205.132:22333/](http://110.42.205.132:22333/)
## OAuth 功能文档
### web登录
请求方式：http(s)://你的url/oauth?oid=XXXXXXXXXXXXXXXXXXXX<br>
参数：
|参数名|方式|说明|
|---|---|---|
|oid|get|你在“OAuth 开发者系统”看到的“应用授权 Openid”|
- - -
返回值：
|参数名|方式|说明|
|---|---|---|
|usrname|-|授权用户的用户名|
|oid|-|你在“OAuth 开发者系统”看到的“应用授权 Openid”|
### 设备认证
#### 生成认证码
请求方式：http(s)://你的url/developer/device?oid=XXXXXXXXXXXXXXXXXXXX<br>
参数：
|参数名|方式|说明|
|---|---|---|
|oid|get|你在“OAuth 开发者系统”看到的“应用授权 Openid”|
- - -
返回值：
|参数名|方式|说明|
|---|---|---|
|status|-|生成状态。`1`为成功,其他数值或空值均为失败|
|code|-|显示给最终用户的认证码，共`8`位|
|openid|-|你在“OAuth 开发者系统”看到的“应用授权 Openid”|
|time|-|当前时间。|
#### 最终用户填写认证码
请求方式：http(s)://你的url/oauth/device<br>
#### 后台循环请求状态
请求方式：http(s)://你的url/developer/device/callback.php?code=XXXXXXXX<br>
参数：
|参数名|方式|说明|
|---|---|---|
|code|get|在“生成认证码”步骤得到的认证码，共`8`位|
- - -
返回值：
|参数名|方式|说明|
|---|---|---|
|status|-|认证状态。`1`为成功,其他数值或空值均为未认证|
|name|-|认证用户的用户名|
|time|-|当前时间。|
