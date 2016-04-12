# 移动端 HTML5 页面常见问题

### 1. 数字键盘
```html
<input type="number" />
<input type="number" pattern="[0-9]*" />
<input type="tel" />
```
效果对应下图  
![手机键盘](../images/keyboard.jpg)
注意：单独使用type="number"时候，iOS上出现并不是九宫格的数字键盘，如果需要九宫格的数字键盘，可选择使用2、3的方法。 上面3种方法均可在Android上唤起九宫格的数字键盘。

### 2. 键盘显示“搜索”按钮
```html
<form action="">
	<input type="search">
</form>	
```

### 3. 去除textarea默认样式
* 去除右下角样式
```css
resize:none;
```
* 去除框外上下空白
```css
vertical-align: middle;
```

### 4. ios&&android系统
* 禁止ios和android用户选中文字
```css
-webkit-user-select: none;
```
* 禁止ios长按时触发系统的菜单，禁止ios&android长按时下载图片
```css
-webkit-touch-callout: none;
```
* webkit去除表单元素的默认样式
```css
-webkit-appearance: none;
```
* 修改表单输入框placeholder的样式
```css
input::-webkit-input-placeholder{color: #ccc;}
input:focus::-webkit-input-placeholder{color: #333;}
```
* 去除android a/button/input标签被点击时产生的边框 & 去除ios a标签被点击时产生的半透明灰色背景
```css
a,button,input{-webkit-tap-highlight-color: rgba(255,0,0,0);}
```
* ios使用-webkit-text-size-adjust禁止调整字体大小
```css
body{-webkit-text-size-adjust: 100%!important;}
```
* android 上去掉语音输入按钮
```css
input::-webkit-input-speech-button {display: none}
```
* 取消input在ios下，输入的时候英文首字母的默认大写
```html
<input autocapitalize="off" autocorrect="off" />
```
* 打电话和发短信
```html
<a href="tel:0755-10086">打电话给:0755-10086</a>
<a href="sms:10086">发短信给: 10086</a>
```

### 5. meta标签
* 移动端页面设置视口宽度等于设备宽度，并禁止缩放。
```html
<meta name="viewport" content="width=device-width,initial-scale=1.0,minimum-scale=1.0,maximum-scale=1.0,user-scalable=no" />
```
* 移动端页面设置视口宽度等于定宽（如640px），并禁止缩放，常用于微信浏览器页面。
```html
<meta name="viewport" content="width=640,initial-scale=1.0,minimum-scale=1.0,maximum-scale=1.0,user-scalable=no" />
```
* 禁止将页面中的数字识别为电话号码
```html
<meta name="format-detection" content="telephone=no" />
```
* 忽略Android平台中对邮箱地址的识别
```html
<meta name="format-detection" content="email=no" />
```
* 当网站添加到主屏幕快速启动方式，可隐藏地址栏，仅针对ios的safari
```html
<meta name="apple-mobile-web-app-capable" content="yes" />
<!-- ios7.0版本以后，safari上已看不到效果 -->
```
* 将网站添加到主屏幕快速启动方式，仅针对ios的safari顶端状态条的样式
```html
<meta name="apple-mobile-web-app-status-bar-style" content="black" />
<!-- 可选default、black、black-translucent -->
```
* 添加到主屏后的标题
```html
<meta name="apple-mobile-web-app-title" content="标题">
```
* 添加智能 App 广告条 Smart App Banner：告诉浏览器这个网站对应的app，并在页面上显示下载banner
```html
<meta name="apple-itunes-app" content="app-id=myAppStoreID, affiliate-data=myAffiliateData, app-argument=myURL"> 
```
* viewport模板
```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<meta content="width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=no" name="viewport">
		<meta content="yes" name="apple-mobile-web-app-capable">
		<meta content="black" name="apple-mobile-web-app-status-bar-style">
		<meta content="telephone=no" name="format-detection">
		<meta content="email=no" name="format-detection">
		<title>title</title>
	</head>

	<body></body>
</html>
```







