---
layout: post
tags: [douban]
---
{% include JB/setup %}
Github API v3设计


转自[Hooopo的日记](www.douban.com/note/249043281/)

```
Github API v3设计
2012-11-25 02:25:24

Hooopo @Hooopo
Github的API v3设计的太赞了！或许是我最近使用公司内部API太多了才会有这种感觉..?

Saito @SaitoWu
@Hooopo Github 业界良心啊.

Hooopo @Hooopo
@SaitoWu 感觉Github的API有点超文本驱动的意思了。目前我们公司的API连正确使用HTTP动词这点都没有共识。

Saito @SaitoWu
@Hooopo 除了 Rails 程序员对于 HTTP verb 偏执之外. 其他 web 程序员都完全不 care verb 这回事. 有的 web 框架后端不区分 GET 与 POST 请求, 更别说 PUT PATCH DELETE 了. 看不惯就撤吧.. orz


Hooopo @Hooopo
@SaitoWu 是哇，程序员在意某个方法的微小性能差异，但对程序整体的伸缩性安全性什么的一点不在意。

Saito @SaitoWu
@Hooopo 这个跟技术背景很有关系, 我有个同学之前是 pure c 的背景. 现在有项目要用到前端. 他很关心 javascript 大对象内存拷贝的事情. 我就从来都没考虑过. 还有些很担心编程语言太灵活好用, 写出来的程序队友看不懂. 这些都是病, 得电.

Hooopo @Hooopo
@__yuan__ http://developer.github.com/v3/#hypermedia 这就是我上次和你讨论的用URI模板发布公共API接口的方式。

Hooopo @Hooopo
@Hooopo @__yuan__ 通过 curl https://api.github.com 返回所有发布的API名称和参数，这样发布API接口就和发布软件接口一样了。发布和升级变得优雅了很多...

Hooopo @Hooopo
http://developer.github.com/v3/#rate-limiting … 给未认证API调用一个很低的请求频率限制，给认证的API请求高的频率限制，并且每次调用在X-RateLimit-Limit提供当前剩余调用次数，保证客户端知道自己的状态。

Hooopo @Hooopo
http://developer.github.com/v3/#conditional-requests … 通过标准的HTTP协议去实现缓存，并且缓存命中时不计入RateLimit。

Hooopo @Hooopo
http://developer.github.com/v3/#json-p-callbacks … JSONP请求返回的Content-Type是application/javascript,普通API调用返回的Content-Type是application/json。好吧 这都是基本的常识，但是很少API接口设置正确。

Hooopo @Hooopo
每个API返回都带一个 X-Content-Type-Options: nosniff 头，这太赞了，程序员应该自己清楚返回的Content-Type，不需要IE的自作聪明...

Saito @SaitoWu
@Hooopo 真正写好 API 要掌握的点非常多啊. 比如 POST 成功的 status 201 设置完之后还得设置一个在 header 里面设置 location. DELETE 成功如果 body 不返回数据要 204 等等. 光 status 就够喝一壶的.

Hooopo @Hooopo
@SaitoWu 嗯 都是HTTP协议的规范呀 可是现在大家都只拿HTTP协议当传输协议。

Saito @SaitoWu
@Hooopo 还好有 Github 这样的, 给开发者也做了表率. 没法强求别人, 先做好自己吧.

http://developer.github.com/v3/
```
