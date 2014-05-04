# Jlazyload 延迟加载

## 零、插件简介
1. 插件名称：Jlazyload
2. 依赖 jQuery 版本：`1.2.6`
3. 预览地址：[fiddle](http://jsfiddle.net/keelii/tghPa/6/)、[jsBin](a)
4. SVN 版本地址：

## 一、HTML 示例
html 代码示例
```html
<div id="load-lazy"></div>
```

## 二、初始化脚本
javascript 代码示例
```javascript
// 图片延迟加载
$("img[data-lazyload]").Jlazyload({
    type:"image",
    placeholderClass:"err-product"
});
```javascript
// 模块延迟加载
$("#module").Jlazyload({
    type:"module"
}, function() {
    // do something
});
```

## 三、参数详情
* type —— 类型值 默认 null,
* offsetParent —— 父元素 默认 null,
* source —— 默认 "data-lazyload",
* placeholderImage —— 占位图片 "http —— 默认 //misc.360buyimg.com/lib/img/e/blank.gif",
* placeholderClass —— 占位元素 class 默认 "loading-style2",
* threshold —— 触发阈值 默认 200

## 四、需要注意的几点
1. 如果 type 设置成 `module`，初始化的对象必须是<abbr title="display:!none">显示</abbr>状态的元素。比如 `display:none` 的元素初始化 Jlazyload 就会发生异常。如果元素必须隐藏可以使用下面的方法：

```javascript
$("#module").wrap('<div data-lazyload="true"></div>').parent().Jlazyload({
    type: 'module'
}, function(s, o) {
    // do something
});
```