MDN实际上是（Mozilla Developer Network）的缩写，它是一个汇集众多Mozilla基金会产品和网络技术开发文档的免费网站。后来换了个名字叫MDN Web Docs。

1992年，美国的NCSA(National Center for Supercomputing Applications，国家超级电脑应用中心)开发了一个叫Mosaic（马赛克）的浏览器，并于1993年发布。

1994年，有一家叫 **马赛克通信公司**（Mosaic Communications Corporation）的公司成立了。

-  同年十月，马赛克通信公司发行了第一个产品：**Mosaic Netscape 0.9**，一个网页浏览器。这个浏览器比其他竞争对手（如Mosaic）好用 ，所以它在短时间内成为了互联网用户的主要浏览器。

- 为了避免和NCSA发布的Mosaic商标拥有权产生问题，这套程序后来改名为Netscape Navigator（“网景导航者”），公司也更名为“网景通信（Netscape Communications ），简称网景（Netscape）。

- 后来网景公司成立 **Mozilla组织**，让它来协调**Mozilla应用包**的开发。**Mozilla组织**是一个**支持和领导开放源代码项目**的一个非营利组织。它拥有一个子公司：Mozilla公司。所以尽管Mozilla组织主要由网景公司的员工组成，但是理论上，它是独立于网景公司运作的。

	- 火狐浏览器（**Mozilla Firefox**）

- 微软干掉了网景，网景被美国在线（AOL）收购，AOL和微软打反垄断的官司赢了，微软提供AOL 7年无限制的使用和散布Internet Explorer的权利，所以AOL解散网景，但同时成立了Mozilla基金会，目的是保证Mozilla组织可以在没有网景以后能继续生存下去。

2004年，AOL关闭了一个受欢迎的开发者网站Netscape DevEdge。  DevEdge曾是一个重要的、有关互联网技术的数据源，它维护了网景浏览器、和诸如HTML和JavaScript技术的帮助文档、以及由业界和技术领导者（如丹尼·古德曼）所编写的文章。之前Mozilla组织的内容是放在这个网站上的。

AOL关闭了网站，但是这些资源不能全部都藏起来。然后，2005年，由Mozilla公司员工Deb Richardson领头，通过Mozilla基金会向AOL获取了DevEdge发布的内容，将他重新发布到Mozilla Developer Center网站，这个网站后来改名，也就是我们现在看到的MDN Web Docs。

2007年底，AOL决定停止网景浏览器的开发，并于2008年3月1日起停止安全更新和所有的技术支持，并建议用户转移使用Firefox浏览器。就此，名噪一时的网景公司彻底被尘封在历史的光阴中了。

网景的重要发明
-   发明了HTTP Cookie技术，使得网站能将数据保存在浏览器中。

-   发明了现在广为使用的JavaScript语言。

-   发明了JAR文件格式，此格式将许多Java class文件压缩成一个文件，并可加上数字签名。

-   制订并在产品中支持传输层安全协议（SSL）。

-   发明的Netcaster技术是"推送技术"（Push technology）先驱。

  
  2020年8月底，Mozilla裁员，MDN文档团队基本上被裁掉了，所以这两年MDN使用wiki平台（多人协作的协作系统）维护文档。
  原本使用的是Kuma平台（开源服务网格框架），但是 (Kuma) 平台复杂且难以维护，添加新功能非常困难。
  
  后来MDN团队将内容从 MySQL 数据库移动在 GitHub 存储库中，我们将使用 GitHub 的贡献工具和功能，实质上是将 MDN 从 Wiki 模型转移到拉取请求 (PR) 模型。这对于贡献来说要好得多，允许智能 linting、大规模编辑以及将 MDN 文档包含在您想要添加到的任何工作流程中（您可以直接在您喜欢的代码编辑器中编辑 MDN 源文件）。
  
 