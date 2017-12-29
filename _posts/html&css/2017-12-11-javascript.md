---
layout: default
title: javascript
categories: html&css
---

#JavaScript
动态类型语言


###window对象
window为全局变量,所有下面都是全局变量的方法,自定义的全局变量也存在window里面
###属性：
  * location:页面的url,改变这个变量就会访问新的页面
  * status:浏览器状态区显示的字符串
  * onload:页面加载完之后调用的函数
  * document:属性包含的dom

###方法：
  * alert:弹窗
  * prompt:带输入框的弹窗
  * open:打开新的浏览器窗口
  * close:关闭窗口,只能关闭javascript打开的窗口
  * setTimeout:指定时间调用处理程序
  * setInterval:指定时间反复调用一个处理程序
  * clearInterval:停止计时器
  * setTimeour:指定时间在运行一次

##document对象
###属性
  * domain:域名
  * title:标题
  * URL:url

###方法
  * getElementById:通过元素id来获取页面的元素
  * getElementByTagName:通过元素标记来获取页面元素列表(<code>head</code>,<code>p</code>,<code>script</code>)
  * getElementByClassName:通过元素的类来获取页元素
  * createElement:创建元素
  * querySelectorAll:获取于CSS选择器(<code>class</code>)参数匹配的元素对象数组

##p元素对象
###属性
  * innerHTML:显示在页面上的文本
  * childElementCount:子元素的数量
  * firstChild:第一个子对象

###方法
  * appendChild:增加子对象
  * replaceChild:替换子对象
  * insertBefore:向前面插入对象
  * setAttribute:设置元素中的属性(src/class/id)
  * getAttribute:获取元素的属性

###有三种方法插入到html标记语言中
  * 放在head标签中,先执行javescript代码,在解析页面
  * 通过script标签的src属性
  * 直接加载script标签中

###JaveScript与页面交互
  * 通过DOM(document Object Model)与页面中的标记交互
  * 修改DOM时,浏览器会动态更新页面

##语句介绍:
  * 使用document表示浏览器中的整个页面
  * window.onload赋值来使页面加载好后执行函数中的代码
  * 通过alert来执行弹窗
  * 存在同名函数的时候,会使用后加载的那一个

###访问元素
  * document.getElementById来访问某个元素,返回一个元素的引用
  * 通过元素.xx 获得元素的属性
  * 通过对属性赋值来改变属性
  * 元素.innerHTML=xx,来改变元素先试的的内容

###创建元素
  * 通过createElement来创建元素,返回一个新元素的引用

###变量
  * 使用var声明变量
  * 以一个字母/下划线/美元符号开头
  * 未赋值的变量是undefined

###数组
  * 使用Array()创建数组
  * 使用length获取数组的大小

###字典:
  * 使用点号'.'来访问字典的元素
  * 使用[]来访问字典的元素
  * delete来删除元素,成功返回true
  * length来获取字典长度


###function:
  * 可以当成一个类来看
  * 对象中使用this表示对象本身

###for
  * 1.类似C++:for(i=0;i!=10;i++)
  * 2.for(i in iter)

##地理位置
  * navigator.geolocation对象是否存在来检验是否支持地理定位API
    * getCurrentPosition:来获取地理位置
    * watchPosition:持续监控位置
    * clearWatch:停止监控
  * 使用navigator.geolocation.getCurrentPosition(func)来获取地理位置
    * 第一个参数为正确是否处理函数,第二个是错误处理函数(默认undefine),第三个是定制地理定位的方法
    * 正确处理的函数参数为一个变量,包含传入的经度和纬度
    * 精度:position.coords.latitude
    * 纬度:position.coords.longitude
    * 精确度(米):position.coords, ourCoords
    * 高度:altitude
    * 高度误差(米):altitudeAccuracy
    * 朝向:heading
    * 速度:speed
  * 获取失败时返回error.code表示失败码:
    * code为0时:不适用1-3时采用的
    * code为1时:拒绝了请求
    * code为2时:无法得到位置信息
    * code为3时:请求超时

##XMLHttpRequest 
  * 用于在后台与服务器交换数据
  * 不重新加载页面的情况下更新网页
  * 页面已加载后从服务器请求数据
  * 页面已加载后从服务器接收数据
  * 后台向服务器发送数据
  * <code>onload</code>处理程序从服务器获得的响应

##JSONP
  * 起因:解决主流浏览器的跨域数据访问的问题,即同源策略(域名,协议,端口相同)引起的问题.
  * 定义:利用<code>&lt;script&gt;</code>元素的这个开放策略，网页可以得到从其他来源动态产生的 JSON 资料
  * 只支持<code>GET</code>请求
  * 返回<code>函数名(数据)</code>

##Json
  * <code>stringify</code>:从一个对象中解析出对象解析为字符串
  * <code>parse</code>:从字符串中解析出<code>Json</code>对象

##画布
  * <code>getContext("2d")</code>:返回一个2D上下文变量
  * <code>fileRect(x,y,w,h)</code>:绘制矩形
  * <code>arc(x,y,r,startRadian,endRadian,direction)</code>:绘制圆弧
  * <code>fillStyle</code>:上下文的一个属性,保存画布上完成绘制所用的颜色
  * <code>beginPath</code>:告诉画布需要开始一个新路径
  * <code>moveTo(x,y)</code>:把笔移动到画布指定的某点
  * <code>lineTo(x,y)</code>:把笔画到指定的某点
  * <code>closePath</code>:关闭路径
  * <code>lineWidth</code>:设置线长
  * <code>fill</code>:填充路径
  * <code>stroke</code>:显示边缘
  * <code>textAlign</code>:文本对齐方式<code>start</code>,<code>end</code>,<code>left</code>,<code>right</code>,<code>center</code>
  * <code>font</code>:设置字体
  * <code>fillText(txt,x,y,maxwidth)</code>:填充文本
  * <code>strokeText(txt,x,y,maxwidth)</code>:笔划文本
  * <code>shadowBlur</code>:设置阴影滤镜大小
  * <code>shadowOffsetX</code>:设置阴影x
  * <code>shadowOffsetY</code>:设置阴影y
  * <code>shadowColor</code>:设置阴影颜色
  * <code>drawImage(img,x,y,w,h)</code>:绘制图像,图像用<code>Image</code>加载,通过赋值<code>onload</code>加载完成后在绘制

##视频
  * <code>onended</code>:播放完视频
  * <code>load</code>:加载视频
  * <code>plya</code>:播放视频
  * <code>canplayType</code>:是否能播放某种类型,能则返回非空字符串,参数包含
    * <code>"video/map4"</code>:mp4格式
    * <code>"video/webm"</code>:webm格式
    * <code>"video/ogg"</code>:ogg格式
  * <code>load</code>:

##注册事件
  * <code>addEventListener(event,func,false)</code>:增加一个事件处理程序