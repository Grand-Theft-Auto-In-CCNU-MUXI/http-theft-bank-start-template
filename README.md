# http-theft-bank-start-template

> 木犀银行抢劫游戏模版 hope this can help you

- [http-theft-bank-start-template](#http-theft-bank-start-template)
  - [To begin with](#to-begin-with)
  - [Tips](#tips)
  - [附录 http](#%E9%99%84%E5%BD%95-http)
    - [URL](#url)
    - [http 工作流程](#http-%E5%B7%A5%E4%BD%9C%E6%B5%81%E7%A8%8B)
    - [http 协议方法](#http-%E5%8D%8F%E8%AE%AE%E6%96%B9%E6%B3%95)
    - [HTTP Header 的介绍](#http-header-%E7%9A%84%E4%BB%8B%E7%BB%8D)
      - [Requests 部分 (request 的 header 简称请求头)](#requests-%E9%83%A8%E5%88%86-request-%E7%9A%84-header-%E7%AE%80%E7%A7%B0%E8%AF%B7%E6%B1%82%E5%A4%B4)
      - [Responses 部分 （response header 简称 响应头）](#responses-%E9%83%A8%E5%88%86-response-header-%E7%AE%80%E7%A7%B0-%E5%93%8D%E5%BA%94%E5%A4%B4)
        - [`cookies`](#cookies)
      - [返回结果的`HTTP`状态码](#%E8%BF%94%E5%9B%9E%E7%BB%93%E6%9E%9C%E7%9A%84http%E7%8A%B6%E6%80%81%E7%A0%81)

## To begin with

请完成游戏。

**序章**

此时你正在敲代码解题，突然，电脑黑屏了，并逐行出现了文字：

```shell
>欢迎参与Backend黑客组织的考核_

>我们已经在暗中观察你很久了_

>也知道你期待加入我们组织_

>现在机会来了_

>请骇入MUXI银行最深处的电子密码门_

>我们会在那里恭候你的光临_
```

文字的最后，出现了一个字符串：

http://http-theft-bank.gtainccnu.muxixyz.com/api/v1/organization/code

似乎是一个网址，用浏览器打开或许能找到一些线索......

## Tips

* 通关游戏，目前一共有 5 个 checkpoint。通关游戏之后会有**明确的提示**。

* 目前模版里有 5 个文件夹，每个 checkpoint 的程序放在对应文件夹里面

  单独一个 main.go 文件，不要改文件名，否则测试无法通过

* 如果是用 github classroom，每推一次仓库（可能）会告诉你有无通过

* **注意把每个 checkpoint 返回的文本信息要输出，自动检测需要**

* 为了更容易通关，需要导入 hacker-support 包 
  
  包地址： https://github.com/Grand-Theft-Auto-In-CCNU-MUXI/hacker-support

* 有能力的可以看服务端源码，等于作弊通关
  
  服务端地址： https://github.com/Grand-Theft-Auto-In-CCNU-MUXI/http-theft-bank

## 附录 http

### URL

**URL** 需要提供的信息有协议名，服务器地址，端口号，路径

```http
http://localhost:8080/helloworld
```

在这里，http 就是协议名，其他的还有 https、FTP、SSH 等

`localhost` 就是**主机地址**，`localhost `表示的是**本机的地址**，又可以写成 `127.0.0.1`。有时，在主机名前也可以包含连接到服务器所需的用户名和密码（格式：`username:password@hostname`）。

而`8080`表示的是**端口号**

后面则是跟着**路径**，一般用来表示主机上的一个目录或文件地址，通常由零或多个`/`隔开的字符串

又如百度的 url 为：https://www.baidu.com

其中 `www.baidu.com` 为其域名。把它解析成一般形式的 url，也是上述的 主机地址+端口号 形式。

[详细介绍](https://blog.csdn.net/hhthwx/article/details/78567961)

### http 工作流程

使用 `http` 常用于 B/S 模型，即 client & server ，一端担任客户端角色，另一端担任服务端角色。

客户端给服务端发送**请求**，服务端收到请求后，做一些处理再返回给客户端一个**响应**。

流程如下：

```shell
                 request
       ----------------------------->
client                                server
       <-----------------------------
                 response
```

值得注意的是请求报文里面有**请求的方法**。例如，`get` ， `post` 等等。在服务端返回的时候会包含一个**状态码**，就是我们平时所熟知的`200`，`404`等等。

### http 协议方法

* GET 用于获取资源

  用来请求访问的资源。

* POST 用来传输实体主体

* PUT 用来传输文件

* DELETE 用来删除文件

* OPTIONS 用来询问支持的方法

* HEAD 获得报文的首部

* PATCH  在请求中定义了一个描述修改的实体的集合，如果被请求修改的资源不存在，服务器可能会创建一个新的资源

### HTTP Header 的介绍

**HTTP头字段**（英语：HTTP header fields）是指在[超文本传输协议](https://zh.wikipedia.org/wiki/超文本传输协议)（HTTP）的请求和响应消息中的消息头部分。它们定义了一个超文本传输协议事务中的操作参数。HTTP头部字段可以自己根据需要定义，因此可能在 Web 服务器和浏览器上发现非标准的头字段。

HTTP 头字段根据实际用途被分为以下 4 种类型：

- 通用头字段(英语：General Header Fields)
- 请求头字段(英语：Request Header Fields)
- 响应头字段(英语：Response Header Fields)
- 实体头字段(英语：Entity Header Fields)\

#### Requests 部分 (request 的 header 简称请求头)

|     Header      |                             解释                             |                       示例                        |
| :-------------: | :----------------------------------------------------------: | :-----------------------------------------------: |
|     Accept      |                 指定客户端能够接收的内容类型                 |           Accept: text/plain, text/html           |
| Accept-Charset  |                 浏览器可以接受的字符编码集。                 |            Accept-Charset: iso-8859-5             |
| Accept-Encoding |     指定浏览器可以支持的web服务器返回内容压缩编码类型。      |          Accept-Encoding: compress, gzip          |
|  Authorization  |                      HTTP授权的授权证书                      | Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ== |
|  Cache-Control  |                 指定请求和响应遵循的缓存机制                 |              Cache-Control: no-cache              |
|   Connection    |      表示是否需要持久连接。（HTTP 1.1默认进行持久连接）      |                 Connection: close                 |
|     Cookie      | HTTP请求发送时，会把保存在该请求域名下的所有cookie值一起发送给web服务器。 |           Cookie: $Version=1; Skin=new;           |
| Content-Length  |                        请求的内容长度                        |                Content-Length: 348                |
|  Content-Type   |                  请求的与实体对应的MIME信息                  |  Content-Type: application/x-www-form-urlencoded  |
|   User-Agent    |            User-Agent的内容包含发出请求的用户信息            |       User-Agent: Mozilla/5.0 (Linux; X11)        |
|      Host       |                指定请求的服务器的域名和端口号                |                Host: www.zcmhi.com                |

#### Responses 部分 （response header 简称 响应头）

|      Header      |                           解释                            |                        示例                         |
| :--------------: | :-------------------------------------------------------: | :-------------------------------------------------: |
|  Cache-Control   |         告诉所有的缓存机制是否可以缓存及哪种类型          |               Cache-Control: no-cache               |
| Content-Encoding |           web服务器支持的返回内容压缩编码类型。           |               Content-Encoding: gzip                |
|  Content-Length  |                       响应体的长度                        |                 Content-Length: 348                 |
|   Content-Type   |                    返回内容的MIME类型                     |       Content-Type: text/html; charset=utf-8        |
|     Expires      |                   响应过期的日期和时间                    |       Expires: Thu, 01 Dec 2010 16:00:00 GMT        |
|     Location     | 用来重定向接收方到非请求URL的位置来完成请求或标识新的资源 |   Location: http://www.zcmhi.com/archives/94.html   |
|    Set-Cookie    |                      设置Http Cookie                      | Set-Cookie: UserID=JohnDoe; Max-Age=3600; Version=1 |

##### `cookies`

由于`http`是一种**无状态的协议**，所以服务器是无法对之前的客户端进行记录的，因此使用了`Cookie`技术，可以得到之前的状态信息。写在了请求和响应的报文内。比如你在登陆了淘宝后，系统再次访问其他页面，倘若需要验证用户权限，不可能让你再次登入，因此使用了这个技术。同理，token的作用也是类似。

#### 返回结果的`HTTP`状态码

* `2XX` 表示成功
  * 200 正常处理
  * 204 处理成功，但是没有资源返回
  * 206 表示客户端进行了范围的请求，服务端也成功执行了这个部分的请求
* `3XX` 表示需要重定向，表明浏览器需要执行某些特殊的处理以正确处理请求
  * 301 表示资源的位置永久更换了
  * 302 表示的是临时更换了位置
* `4XX` 表示客户端错误
  * 400 表示请求报文内存在语法错误
  * 401 表示认证失败，页面需要认证信息
  * 403 表示访问被服务端拒绝了
  * 404 表示服务器上没有请求的资源
* `5XX` 表示服务器的错误
  * 500 表示服务端本身的问题
  * 503 表示服务端暂时处于超载或者停机维护

