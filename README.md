# ElasticHD
Fixed POST header problem. 解决了新版本es发送POST请求时返回的header错误问题。

Solved the content-type header triggered when sending a POST request in a high version client. You can download the executable file version according to your needs. Linux or Mac version. The execution method is the same as the original: https://github.com/qax-os/ElasticHD

解决了高版本es客户端，发送POST请求时触发的 Content-Type header 问题。
可以根据需求，下载对应的执行文件版本。Linux 或 Mac 版本。
执行方法与原版一样 https://github.com/qax-os/ElasticHD
```
./main -p host:port
```

# 源码解决方案
将 ElasticHD/main/vendor/github.com/mattbaird/elastigo/lib/connection.go 目录下的第159行的代码
```
req.Header.Add("Accept", "application/json")
```
替换成下面的代码，即可源码运行
```
req.Header.Add("Accept", "*/*")
req.Header.Add("Content-Type", "application/json")
```
