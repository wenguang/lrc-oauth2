https://mp.weixin.qq.com/s/p_D3opcYZh3aWbWqMAVG9Q
【推荐】一张图搞定OAuth2.0（通俗易懂）

Q、mobile native app、前后端分离的SPA与传统的web app在授权模式上有什么不同，它们有什么问题
A、主要有以下个问题：
    1、OAuth2.0依赖重定向支持细节，这是浏览器的特性（OAuth最开始是没有考虑到移动端的）
    2、使用URI scheme与Intent在应用间跳转 或 模拟web端，使用移动端浏览器与WebView。
    无论哪种方法都需要保证

        跳转目标的确定性，即保证跳转到的应用真的是发起者要去访问的应用；
        跳转请求来源的真实性，即跳转请求发起者的身份是真实可信的；
    3、移动端无法安全存储app secret（这里的app非指手机上的app，而指授权请求者整个应用）
    4...
    5...
    这篇文章说得到位：https://www.jianshu.com/p/ca3fc5890b05（如何在移动端开发中正确地使用OAuth协议：常见错误剖析 - 简书）

Q、客户端（mobile native app、桌面客户端、SPA）有什么好的实现OAuth的方法
A、PKCE模式是个选择，它的核心是即使app secret和Authorization Code被截取也无法获取Access Token，（参考：https://tonyxu.io/zh/posts/2018/oauth2-pkce-flow/）但它似乎只是解决上面的第3个问题

Q、授权过程的安全问题（CSRF攻击）
A、通过state参数、client_id、client_secret解决，参考：http://insights.thoughtworkers.org/attack-aim-at-oauth2/

Q、token的传递方式
A、RFC6750，参考：http://www.cnblogs.com/linianhui/p/oauth2-authorization.html#auto_id_19

Q、token的撤销
A、RFC7009，参考：https://www.cnblogs.com/linianhui/p/oauth2-extensions-protocol-and-json-web-token.html#auto_id_3

Q、token的元数据
A、RFC7662，参考：https://www.cnblogs.com/linianhui/p/oauth2-extensions-protocol-and-json-web-token.html#auto_id_4

Q、JWT在其中的应用
A、RFC7519，参考：https://www.cnblogs.com/linianhui/p/oauth2-extensions-protocol-and-json-web-token.html#auto_id_5

以上RFC文档入口可从 https://oauth.net/2 找到

