---
layout: default
title: flask
categories: html&css
---

#flask
  * 轻量级 Web 应用框架
  * 核心简单
  * 可扩展性强

##Flask
  * 通过Flask创建一个服务端事例
  * 参数是程序的根目录,通过根目录索引相对路径找到资源和配置文件
  * 主要有如下四个上下文
    * <code>current_app</code>:当前激活程序的程序实例
    * <code>g</code>:处理请求时用作临时存储对象,每次请求都会重设这个变量
    * <code>request</code>:请求对象,封装了客户端发出的HTTP请求中的内容
    * <code>session</code>:用于会话,用于存储请求之间需要"记住"的值的词典


因为浏览器会设置缓存,所以在从web服务器获取数据的时候,需要加上可变的参数,有如下几种方法
  * 时间:<code>new Data().getTimer()</code>
  * 随机数:<code>Marh.randowm()</code>

##route装饰器
使用route装饰器来决定网址
  * <code>&lt;variable_name&gt;</code>:表示给解析地址的函数传入一个参数
  * <code>&lt;converter:variable_name&gt;</code>:converter来指定转换器,包含以下几种
    * string:没有斜杠的文本
    * int:整型
    * float:浮点型
    * path:接受斜杠的文本
    * uuid:uuid字符串
  * 包含转换器解析不匹配时,打开网页失败(404)
  * <code>/</code>截至的url,会在用户未输入<code>/</code>时候自动跳转到<code>/</code>页面
  * 没有<code>/</code>截至的url,用户输入<code>/</code>时候会出现**404**

##errorhandler装饰器
使用<code>errorhandler</code>装饰器来处理错误情况

##url_for函数
  * 原型<code>url_for(endpoint, **values)</code>
  * 第一个参数<code>endpoint</code>来匹配现有的函数,通过调用<code>route</code>装饰器装饰的函数来产生一个网址
  * 第二个参数是传递给函数的参数
  * 通过<code>url_for</code>更高的可维护和可扩展性
  * 通过<code>url_for</code>函数将会透明的处理特殊字符和Unicode数据转换
  * 通过<code>url_for</code>将应用程序和网页目录分离

##HTTP方法
  * <code>GET</code>:
    * 请求的数据附在URL之后,以?分割URL和传输数据，参数之间以&相连
    * HTTP协议规范没有对URL长度进行限制,但受到浏览器对于URL长度的限制
    * 数据显示在URL中,安全性低
    * 产生一个TCP数据包,把http header和data一并发送出去,服务器响应200
  * <code>POST</code>:
    * 提交的数据则放置在是HTTP包的包体中
    * 没有大小限制的，HTTP协议规范也没有进行大小限制
    * 数据不显示在URL中,安全性较高
    * 产生二个TCP数据包.浏览器先发送header,服务器响应100;浏览器再发送data,服务器响应200.
  * <code>HEAD</code>:
    * 只请求页面的首部,用于搜索引擎
    * Flask中按照<code>GET</code>方式即可,但不传递实际内容
  * <code>PUT</code>:
    * 多次传输来覆盖存储过程
    * 传输过程中可能连接丢失,多次更加保证数据有效
  * <code>DELETE</code>: 请求服务器删除指定的页面

##current_app
当前激活程序的程序实例

##request
请求对象,封装了客户端发出的HTTP请求中的内容

####属性
  * <code>url_charset</code>:获取编码,默认<code>utf-8</code>
  * <code>want_form_data_parsed</code>:
  * <code>remote_addr</code>:客户端的远程地址
  * <code>stream</code>:获取原始的字节流
  * <code>args</code>:
  * <code>method</code>:数据传输的方式(<code>POST</code>/<code>GET</code>)
  * <code>data</code>:<code>get_data</code>有默认的效果
  * <code>values</code>:获取<code>GET</code>方法<code>?</code>后的<code>key</code><code>value</code>数据
  * <code>files</code>:上传过来的文件数据
  * <code>cookies</code>:浏览器为了辨别用户身份存储在用户本地终端上的数据，而这些数据通常会经过加密处理,服务器可以访问
  * <code>headers</code>:头部信息,一般包含
    * <code>Host</code>:主机ip
    * <code>Connection</code>:涟接方式
    * <code>Cache-Control</code>:定所有缓存机制在整个请求/响应链中必须服从的指令,用于阻止缓存对请求或响应造成不利干扰的行为
    * <code>Upgrade-Insecure-Requests</code>:加载<code>http</code>资源时自动替换成<code>https</code>请求开关(<code>https</code>页面允许出现<code>http</code>请求)
    * <code>User-Agent</code>:用于识别用户的操作系统/浏览器等信息
    * <code>Accept</code>:声明浏览器支持的数据类型
    * <code>Accept-Encoding</code>:声明浏览器支持的编码类型
    * <code>Accept-Language</code>:声明浏览器支持的语言,<code>q</code>表示对语言的喜好程度
    * <code>Cookie</code>:用户信息缓存
  * <code>path</code>:路径信息,不包括请求的信息
  * <code>full_path</code>:整个路径(解码为unicode),包括请求的信息(<code>?</code>后面的内容)
  * <code>script_root</code>:脚本的根地址?!
  * <code>url</code>:整个路径
  * <code>base_url</code>:不带参数的<code>url</code>
  * <code>url_root</code>:<code>url</code>的根地址
  * <code>host_url</code>:主机<code>url</code>
  * <code>host</code>:主机ip:端口
  * <code>access_route</code>:主机<code>ip</code>(列表)
  * <code>remote_addr</code>:主机<code>ip</code>(字符串)
  * <code>accept_mimetypes</code>:用户可以接受的文件格式
  * <code>accept_charsets</code>:用户可以接受的字符集
  * <code>accept_encodings</code>:用户可以接受的编码
  * <code>accept_languages</code>:用户可以接受的语言
  * <code>cache_control</code>:接受的头信息里面的缓存控制信息
  * <code>if_match</code>:
  * <code>if_none_match</code>:
  * <code>if_modified_since</code>:
  * <code>if_unmodified_since</code>:
  * <code>if_range</code>:
  * <code>range</code>:
  * <code>user_agent</code>:用户的UA信息
  * <code>authorization</code>:授权信息
  * <code>content_length</code>:
  * <code>mimetype</code>:
  * <code>mimetype_params</code>:
  * <code>pragma</code>:
 
####类方法
  * <code>from_values</code>:
  * <code>application</code>:
  * <code>flash</code>:类似<code>alert</code>

##模版
  * 默认情况下,Flask在程序文件夹的<code>templates</code>子文件夹中寻找模版
  * 使用<code>render_template</code>函数把Jinja2模版引擎集成到程序中
    * 第一个参数是模版文件名
    * 后续时模版的键值对,表示模版中真实的值
  * 可以使用**过滤器**来修改变量,添加在变量名之后,中间用竖线分隔

##蓝本
  * 定义的路由处于休眠状态,直到蓝本注册到程序上的时候,路由才会称为真正的程序
  * 通过实例化<code>Blueprint</code>来创造蓝本
  * 第一个参数为命名空间