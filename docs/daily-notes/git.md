# git

### 错误： git SSL certificate problem: unable to get local issuer certificate

#### 这个问题是由于没有配置信任的服务器 HTTPS 验证。默认，cURL 被设为不信任任何 CAs，就是说，它不信任任何服务器验证。

#### 解决办法: 将 https 的 ssl 验证设为 false 不进行 ssl 验证

```git
git config --global http.sslVerify false
```
