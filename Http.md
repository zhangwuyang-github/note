# 浏览器从请求到出界面的一系列动作

重定向 => 拉取缓存 => DNS查询 => 建立TCP链接 => 发起请求 => 接收相应 => 处理HTML元素 => 元素完成加载

## 缓存

存放在内存中的缓存随着进程结束会被清除，存放在硬盘中的不会。可以指定Header中的Etag字段来控制缓存的位置，Expires字段控制生效的时间。

# 项目优化

- 压缩HTML，CSS，JS代码
- 提取公共资源
- webpack开发环境修改为生产环境，会剔除调试代码
- 尽量不要在HTML中缩放图片
- 使用雪碧图
- 小图标使用字体图标，如iconfont
- 使用WebP格式图片
- 使用CDN进行加速
- 路由懒加载，优化开屏时间
- 使用缓存

# 常见请求头

Accept: 浏览器接收文件类型；Connection： 打开网页后要不要关闭（keep alive / close）；Host： 主机端口号；Refer：来源页面信息；User-Agent：客户端浏览器版本信息；Cache-Control： 缓存设置；Cookie：用户身份信息；Range：bytes：0-5请求对象的部分。

# 常见响应头

Cache-Control；Date；Server；Transfer-Encoding：分块发送，长度为0时结束；Expires：缓存有效时间，没有max-age稳定；Connection；Access-Control-Allow-Origin：跨域设置；Etag：验证文件是否被修改；Access-Control-Allow-Methods：允许访问方法；Access-Control-Allow-Credentials：是否允许发送cookie。

# http1 与 http2

1. http2使用二进制对文件进行传送，http1使用文本格式；
2. http2支持多路复用，通过标识流id来定位属于哪个http请求；
3. http2支持头部压缩，使用gzip和compress压缩头部后再发送；
4. http2支持服务器推送，可以在客户端未经许可的情况下主动向客户端推送内容。