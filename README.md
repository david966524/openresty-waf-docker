# openresty-waf-docker
docker-compose 启动 openresty-waf-docker
## config.lua配置文件说明
```
RulePath = "/usr/local/nginx/conf/waf/wafconf/"
--规则存放目录
attacklog = "off"
--是否开启攻击信息记录，需要配置logdir
logdir = "/usr/local/nginx/logs/hack/"
--log存储目录，该目录需要用户自己新建，切需要nginx用户的可写权限
UrlDeny="on"
--是否拦截url访问（如果你用了phpmyadmin，开启此项会有问题）
Redirect="on"
--是否拦截后重定向
CookieMatch = "on"
--是否拦截cookie攻击
postMatch = "on"
--是否拦截post攻击（如果开启，可能会导致网站后台无法正常上传文件）
whiteModule = "on"
--是否开启URL白名单
black_fileExt={"php","jsp"}
--填写不允许上传文件后缀类型
ipWhitelist={"127.0.0.1"}
--ip白名单，多个ip用逗号分隔
ipBlocklist={"1.0.0.1"}
--ip黑名单，多个ip用逗号分隔
CCDeny="on"
--是否开启拦截cc攻击(需要nginx.conf的http段增加lua_shared_dict limit 10m;)
CCrate = "100/60"
--设置cc攻击频率，单位为秒.
--默认1分钟同一个IP只能请求同一个地址100次
html=[[Please go away~~]]
--警告内容,可在中括号内自定义
备注:不要乱动双引号，区分大小写
```
