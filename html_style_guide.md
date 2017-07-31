<font face="微软雅黑" size="4" ><font size="6">前端开发规范之：HTML书写规范</font>
****
>制定小组：58无线FE  
>版本：第一版  
>最后更新：2016-8-8  

## 1 基本准则

* 永远遵循同一套编码规范  
* 尽量遵循 HTML 标准和语义，但是不要以牺牲实用性为代价。  
* 任何时候都要尽量使用最少的标签并保持最小的复杂度。  
* 页面的 结构、样式、行为三者相分离。确保文档或模板中只包含html，把用到的样式都写到样式表文件中，把脚本都写到js文件中  

## 2 代码风格


### 2.1 缩进与换行


#### [建议] 使用4（或2）个空格做为一个缩进层级，减少tab字符的使用。

解释：   

这是唯一能保证在所有环境下获得一致展现的方法。


### 2.2 命名

#### [强制] 元素 `id` 必须保证页面唯一。

解释：  
同一个页面中，不同的元素包含相同的 `id`，不符合 `id` 的属性含义。并且使用 `document.getElementById` 时可能导致难以追查的问题。

#### [强制] 同一页面，应避免使用相同的 `name` 与 `id`。

解释：  
IE 浏览器会混淆元素的 `id` 和 `name` 属性， `document.getElementById` 可能获得不期望的元素。

#### [建议] `id`、`class` 命名，建议单词全字母小写，单词间以 `-` 分隔。在避免冲突并描述清楚的前提下尽可能短。


### 2.3 标签


#### [强制] 标签名必须使用小写字母。

示例：

		<!-- good -->
		<p>Hello StyleGuide!</p>
		
		<!-- bad -->
		<P>Hello StyleGuide!</P>

#### [强制] 对于无需自闭合的标签，不允许自闭合。

解释：  

常见无需自闭合标签有 `input`、`br`、`img`、`hr` 等。

示例：

		<!-- good -->
		<input type="text" name="title">
		
		<!-- bad -->
		<input type="text" name="title" />

#### [强制] 对 `HTML5` 中规定允许省略的闭合标签，不允许省略闭合标签。

示例：

		<!-- good -->
		<ul>
		    <li>first</li>
		    <li>second</li>
		</ul>
		
		<!-- bad -->
		<ul>
		    <li>first
		    <li>second
		</ul>


#### [强制] 标签使用必须符合标签嵌套规则。

解释：  

几种常见标签嵌套规范（详细的标签嵌套规则参见[HTML DTD](http://www.cs.tut.fi/~jkorpela/html5.dtd)中的 `Elements` 定义部分）：
  
1. 块元素可以包含内联元素或某些块元素，但内联元素却不能包含块元素，它只能包含其它的内联元素。例如：a元素在HTML 5规范中，是可以包含块级元素的，如果a包含任何块级元素（如p），则a自动升级为block元素。  

2. p、dt只能包含内嵌元素，不能再包含块级元素的标签

3. `tbody` 必须置于 `table` 中

3. h1、h2、h3、h4、h5、h6包含块级元素,虽然浏览器可以解析正常，但是从语义上讲h元素本身是标题，里面应该放内嵌元素

4. li 内可以包含 div 标签

5. 块级元素与块级元素并列、内嵌元素与内嵌元素并列

6. 不能在列表元素`<li><dt><dd>`等插入非列表兄弟元素



#### [建议] HTML 标签的使用应该遵循标签的语义。

下面是常见标签语义

		- p - 段落
		- h1,h2,h3,h4,h5,h6 - 层级标题
		- strong,em - 强调
		- ins - 插入
		- del - 删除
		- abbr - 缩写
		- code - 代码标识
		- cite - 引述来源作品的标题
		- q - 引用
		- blockquote - 一段或长篇引用
		- ul - 无序列表
		- ol - 有序列表
		- dl,dt,dd - 定义列表

#### [建议] 标签的使用应尽量简洁，减少不必要的标签。

示例：

	<!-- good -->
	<img class="avatar" src="image.png">
	
	<!-- bad -->
	<span class="avatar">
	    <img src="image.png">
	</span>

### 2.4 属性


#### [强制] 属性名必须使用小写字母。


#### [强制] 属性值必须用双引号包围。

解释：  

不允许使用单引号，不允许不使用引号。


#### [建议] 布尔类型的属性，建议不添加属性值。

示例：

		<input type="text" disabled>
		<input type="checkbox" value="1" checked>

#### [建议] 自定义属性建议以 `xxx-` 为前缀，推荐使用 `data-`。

解释：  

使用前缀有助于区分自定义属性和标准定义的属性。

示例：

		<ol data-ui-type="Select"></ol>

## 3 通用


### 3.1 DOCTYPE


#### [强制] 使用 `HTML5` 的 `doctype` 来启用标准模式，建议使用大写的 `DOCTYPE`。

示例：

    <!DOCTYPE html>


#### [建议] 启用 IE Edge 模式。(强烈的特殊需求除外)

示例：

    <meta http-equiv="X-UA-Compatible" content="IE=Edge">


#### [建议] 在 `html` 标签上设置正确的 `lang` 属性。

解释：  

有助于提高页面的可访问性，如：让语音合成工具确定其所应该采用的发音，令翻译工具确定其翻译语言等。

示例：

    <html lang="zh-CN">


### 3.2 编码


#### [强制] 页面内容编码必须采用utf-8编码（特殊需求除外），明确指定字符编码。指定字符编码的 `meta` 必须是 `head` 的第一个直接子元素。

#### [建议] 尽量通过meta标签明确指定字符编码。

#### [强制] 指定字符编码的 `meta` 必须是 `head` 的第一个直接子元素。

示例：

    <html>
        <head>
            <meta charset="UTF-8">
            ......
        </head>
        <body>
            ......
        </body>
    </html>

### 3.3 CSS 和 JavaScript 引入


#### [强制] 引入 `CSS` 时必须指明 `rel="stylesheet"`。

示例：

    <link rel="stylesheet" href="page.css">


#### [建议] 引入 `CSS` 和 `JavaScript` 时无须指明 `type` 属性。

解释：  

`text/css` 和 `text/javascript` 是 `type` 的默认值。

#### [建议] 在 `head` 中引入页面需要的所有 `CSS` 资源。  

解释：  

在页面渲染的过程中，新的CSS可能导致元素的样式重新计算和绘制，页面闪烁。

#### [建议] 展现定义放置于外部 `CSS` 中，行为定义放置于外部 `JavaScript` 中。

#### [建议] `JavaScript` 应当放在页面末尾，或采用异步加载。

解释：  

将 `script`放在页面中间将阻断页面的渲染。出于性能方面的考虑，如非必要，请遵守此条建议。

示例：

    <body>
        <!-- a lot of elements -->
        <script src="init-behavior.js"></script>
    </body>


#### [建议] 移动环境或只针对现代浏览器设计的 Web 应用，如果引用外部资源的 `URL` 协议部分与页面相同，建议省略协议前缀。

解释：  

使用 `protocol-relative URL` 引入 CSS，在 `IE7/8` 下，会发两次请求。是否使用 `protocol-relative URL` 应充分考虑页面针对的环境。

示例：

    <script src="//s1.bdstatic.com/cache/static/jquery-1.10.2.min_f2fb5194.js"></script>

## 4 head


### 4.1 title


#### [强制] 页面必须包含 `title` 标签声明标题。

#### [强制] `title` 必须作为 `head` 的直接子元素，并紧随 `charset` 声明之后。

解释：  
`title` 中如果包含 ASCII 之外的字符，浏览器需要知道字符编码类型才能进行解码，否则可能导致乱码。


示例：

    <head>
        <meta charset="UTF-8">
        <title>页面标题</title>
    </head>


### 4.2 favicon


#### [强制] 保证 `favicon` 可访问。

解释：

在未指定 favicon 时，大多数浏览器会请求 Web Server 根目录下的 `favicon.ico` 。为了保证 favicon 可访问，避免 404，必须遵循以下两种方法之一：

1. 在 Web Server 根目录放置 `favicon.ico` 文件。
2. 使用 `link` 指定 favicon。


示例：

    <link rel="shortcut icon" href="path/to/favicon.ico">

### 4.3 viewport

#### [建议] 若页面欲对移动设备友好，需指定页面的 `viewport`。

解释：

viewport meta tag 可以设置可视区域的宽度和初始缩放大小，避免在移动设备上出现页面展示不正常。

比如，在页面宽度小于 `980px` 时，若需 iOS 设备友好，应当设置 viewport 的 `width` 值来适应你的页面宽度。同时因为不同移动设备分辨率不同，在设置时，应当使用 `device-width` 和 `device-height` 变量。

另外，为了使 viewport 正常工作，在页面内容样式布局设计上也要做相应调整，如避免绝对定位等。关于 viewport 的更多介绍，可以参见 [Safari Web Content Guide的介绍](https://developer.apple.com/library/mac/documentation/AppleApplications/Reference/SafariWebContent/UsingtheViewport/UsingtheViewport.html#//apple_ref/doc/uid/TP40006509-SW26)


## 5 标签选择

#### [建议] 不使用已经废弃的标签 ，如`<center>`等

#### [建议] 尽量不要使用colspan，rowspan两个属性。  

解释：  

这两个属性会引起兼容性问题  

#### [建议] 减少table布局的使用  

解释：  
  
对于整体页面的布局，大部分情况下不要使用table进行布局；但是不是绝对的，对于小范围的布局以及数据表类的情况，可以根据情况合适的选用table布局。

## 6 图片


#### [强制] 禁止 `img` 的 `src` 取值为空。延迟加载的图片也要增加默认的 `src`。

解释：

`src` 取值为空，会导致部分浏览器重新加载一次当前页面，参考：<https://developer.yahoo.com/performance/rules.html#emptysrc>


#### [建议] 避免为 `img` 添加不必要的 `title` 属性。

解释：

多余的 `title` 影响看图体验，并且增加了页面尺寸。

#### [建议] 为重要图片添加 `alt` 属性。

解释：  

可以提高图片加载失败时的用户体验。

#### [建议] 添加 `width` 和 `height` 属性，以避免页面抖动。

#### [建议] 有下载需求的图片采用 `img` 标签实现，无下载需求的图片采用 CSS 背景图实现。

解释：

1. 产品 logo、用户头像、用户产生的图片等有潜在下载需求的图片，以 `img` 形式实现，能方便用户下载。
2. 无下载需求的图片，比如：icon、背景、代码使用的图片等，尽可能采用 CSS 背景图实现。


## 7 表单

### 7.1 控件标题


#### [强制] 有文本标题的控件必须使用 `label` 标签将其与其标题相关联。

解释：

有两种方式：

1. 将控件置于 `label` 内。
2. `label` 的 `for` 属性指向控件的 `id`。

推荐使用第一种，减少不必要的 `id`。如果 DOM 结构不允许直接嵌套，则应使用第二种。

示例：

    <label><input type="checkbox" name="confirm" value="on"> 我已确认上述条款</label>
    <label for="username">用户名：</label> <input type="textbox" name="username" id="username">



  
### 7.2 按钮


#### [强制] 使用 `button` 元素时必须指明 `type` 属性值。

解释：

`button` 元素的默认 `type` 为 `submit`，如果被置于 `form` 元素中，点击后将导致表单提交。为显示区分其作用方便理解，必须给出 `type` 属性。


示例：

    <button type="submit">提交</button>
    <button type="button">取消</button>


#### [建议] 尽量不要使用按钮类元素的 `name` 属性。

解释：  

由于浏览器兼容性问题，不能保证带有 `name` 属性的 `button` 或 `input` 元素的 `value` 属性值在所有浏览器中都可以被提交到服务端。具体情况可参考[此文](http://w3help.org/zh-cn/causes/CM2001)。



### 7.3 可访问性  

#### [建议] 负责主要功能的按钮在 DOM 中的顺序应靠前。

解释：

负责主要功能的按钮应相对靠前，以提高可访问性。如果在 CSS 中指定了 `float: right` 则可能导致视觉上主按钮在前，而 DOM 中主按钮靠后的情况。

示例：

	<!-- good -->
	<style>
	.buttons .button-group {
	    float: right;
	}
	</style>
	
	<div class="buttons">
	    <div class="button-group">
	        <button type="submit">提交</button>
	        <button type="button">取消</button>
	    </div>
	</div>
	
	<!-- bad -->
	<style>
	.buttons button {
	    float: right;
	}
	</style>
	
	<div class="buttons">
	    <button type="button">取消</button>
	    <button type="submit">提交</button>
	</div>

#### [建议] 当使用 JavaScript 进行表单提交时，如果条件允许，应使原生提交功能正常工作。

解释：

当浏览器 JS 运行错误或关闭 JS 时，提交功能将无法工作。如果正确指定了 `form` 元素的 `action` 属性和表单控件的 `name` 属性时，提交仍可继续进行。

示例：

    <form action="/login" method="post">
        <p><input name="username" type="text" placeholder="用户名"></p>
        <p><input name="password" type="password" placeholder="密码"></p>
    </form>


#### [建议] 在针对移动设备开发的页面时，根据内容类型指定输入框的 `type` 属性。

解释：

根据内容类型指定输入框类型，能获得能友好的输入体验。

示例：

    <input type="date">

### 7.4 其他
#### [强制] 表单中的控件的 `id` 或 `name` 不能设置为 `action` 或 `submit`。  

解释：  

如果将指定`input`标签的`id`或者`name`属性值为`action`或`submit`，提交表单时会触发非常隐藏的bug,具体情况可参考[此文](http://blog.jobbole.com/68739/)。

示例：  

        <form id="form" action="url">  
            <input type="text" id="submit">  
        </form>
        // Grab the form  
        var form = document.getElementById('form');  
         
        // Try to submit it the normal way  
        form.submit(); // Nope, that's an error  

#### [建议] 使用 `fieldset`, `legend` 组织表单。


#### [建议] 提交表单操作可以选用下面三类控件

示例：  

    <form action="/login" method="post">
      <input type="submit" value="提交">
      <input type="image" src="pic.png">
      <button>submit</button>
    </form>


## 8 多媒体


#### [建议] 当在现代浏览器中使用 `audio` 以及 `video` 标签来播放音频、视频时，应当注意格式。

解释：

音频应尽可能覆盖到如下格式：

* MP3
* WAV
* Ogg

视频应尽可能覆盖到如下格式：

* MP4
* WebM
* Ogg

#### [建议] 在支持 `HTML5` 的浏览器中优先使用 `audio` 和 `video` 标签来定义音视频元素。

#### [建议] 使用退化到插件的方式来对多浏览器进行支持。

示例：

    <audio controls>
        <source src="audio.mp3" type="audio/mpeg">
        <source src="audio.ogg" type="audio/ogg">
        <object width="100" height="50" data="audio.mp3">
            <embed width="100" height="50" src="audio.swf">
        </object>
    </audio>

    <video width="100" height="50" controls>
        <source src="video.mp4" type="video/mp4">
        <source src="video.ogg" type="video/ogg">
        <object width="100" height="50" data="video.mp4">
            <embed width="100" height="50" src="video.swf">
        </object>
    </video>


#### [建议] 只在必要的时候开启音视频的自动播放。


#### [建议] 在 `object` 标签内部提供指示浏览器不支持该标签的说明。

示例：

    <object width="100" height="50" data="something.swf">DO NOT SUPPORT THIS TAG</object>

## 9 工具  

1. 校验html代码是否符合标准：[校验工具](http://validator.w3.org/)

2. 前端开发工具，检查是否有标签没有闭合，id是否重名，嵌套是否过深等： [web前端助手chrome插件](https://chrome.google.com/webstore/detail/web%E5%89%8D%E7%AB%AF%E5%8A%A9%E6%89%8Bfehelper/pkgccpejnmalmdinmhkkfafefagiiiad?hl=zh-CN)

## 10 参考文章：  

1. [ecomfe-HTML编码规范](https://github.com/ecomfe/spec/blob/master/html-style-guide.md)  

2. [编码规范 by @mdo](http://codeguide.bootcss.com/) 

 
</font>
  
******

