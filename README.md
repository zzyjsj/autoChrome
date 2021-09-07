## chromium爬虫

### 基本功能
获取网页基本信息包块iframe,initUrl,html,title,desc,trueUrl

### 重要功能：
- 能设置是否带上referer头，目前支持baidu和Sogou的referer,**可以通过js检测**
- 每次获得一个page,增加50秒超时时间，来避免chromium的bug  所以配置文件中的超时不能超过50s
- 每隔两个小时，重启一次chromium
- 每隔10s 且当前没有任务执行 ping一次chromium来保活，当无法ping通，重启chromium
- 打开页面超过配置得次数的时候，重启一次chromium

### http接口

```
发送任务
curl -X POST -i 'http://127.0.0.1:7999' --data '{"urls":["http://www.baidu.com","http://www.sodtjww.cn/"],"refer":false}'
获取当前chrome 状态
curl -X GET -i 'http://127.0.0.1:17999/num'
{"currentNum":0,"pagePoolNum":3}
```
### 使用
直接执行exe 文件即可测试使用。默认会去查找或下载chromium。
配置文件提供refer并不能启用自带refer,需要请求的时候带上 ```"refer":true```
