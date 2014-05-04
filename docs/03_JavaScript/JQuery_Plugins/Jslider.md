# Jslider

## 零、插件简介
1. 插件名称：Jslider
2. 依赖 jQuery 版本：`1.2.6`
3. 预览地址：[fiddle](http://jsfiddle.net/keelii/gfANW/10/)、[jsBin](http://jsbin.com/oxAB/1/)
4. SVN 版本地址：

## 一、HTML 示例
html 代码示例
```html
<div id="g-scroll"></div>
<!--广告位数据-->
<script>
var data = [{
    src: "http://img11.360buyimg.com/da/g13/M00/07/0E/rBEhU1IWu2AIAAAAAABy3ObwjHcAACWWwHXsUMAAHL0479.jpg",
    alt: "1",
    href: "http://c.fa.jd.com/adclick?sid=4&cid=353&aid=3248&bid=0&unit=34632&advid=44366&guv=&url=http://sale.jd.com/mall/kxc6HDwfEMUvui.html"
}, {
    src: "http://img14.360buyimg.com/da/g13/M08/07/12/rBEhVFIXJbEIAAAAAAAvZCLxeM0AACYAgMpHlcAAC98419.jpg",
    alt: "2",
    href: "http://c.fa.jd.com/adclick?sid=4&cid=353&aid=3248&bid=0&unit=34631&advid=44365&guv=&url=http://sale.jd.com/act/ilhesCESFWkw.html"
}, {
    src: "http://img14.360buyimg.com/da/g15/M02/05/17/rBEhWVITKf4IAAAAAAAhpGApMf8AACQCwEB3TUAACG8315.jpg",
    alt: "3",
    href: "http://c.fa.jd.com/adclick?sid=4&cid=353&aid=3248&bid=0&unit=34633&advid=46413&guv=&url=http://sale.jd.com/act/FVPYhGgUIbNOeq.html"
}];
<script>
```

## 二、初始化脚本
javascript 代码示例
```javascript
// 焦点图模板
var slideTPL = {
    itemsWrap: '<ul class="slide-items">{innerHTML}</ul>',
    itemsContent: '{for item in json}<li><a href="${item.href}" target="_blank"><img src="${item.src}" alt="${item.alt}" /></a></li>{/for}',
    controlsWrap: '<div class="slide-controls"><div class="controls-inner">{innerHTML}</div></div>',
    controlsContent: '{for item in json}<b>${item_index}</b>{/for}'
};
// 焦点图初始化
$('#g-scroll').Jslider({
    slideWidth: 200,
    slideHeight: 430,
    slideDirection: 1,
    data: data,
    template: slideTPL
}, function(obj) {
    // callback here
});
```

## 三、参数详情
* auto —— 自动播放 默认false
* reInit —— 重新初始化 默认 false
* data —— 传入数据 默认 []
* defaultIndex —— 起始下标 默认 0
* slideWidth —— 宽度 默认 0
* slideHeight —— 高度 默认 0
* slideDirection —— 播放方式 默认 1,//1,left;2,up;3,fadeIn
* speed —— 速度 默认 "normal"
* stay ——  默认 5000
* delay —— 延迟 默认 150
* maxAmount —— 最大帧数 默认 null
* template —— 焦点图模板 默认 null
* showControls —— 显示1,2,3,4按钮 默认 true

## 四、需要注意的几点
1. 插件必须传数据和模板参数 data, template
2. 模板中 *Wrap 字段中 `{innerHTML}` 会被自动替换成对应 *Content 渲染后的 HTML 字符串
3. 插件默认不支持 lazyload， 需要的话可以在回调函数中实现
