## 零、插件简介
1. 插件名称：**Jcal**
2. 依赖 jQuery 版本：`1.2.6`
3. 预览地址：[jsFiddle](http://jsfiddle.net/keelii/axeD9/1/), [jsBin](http://jsbin.com/ONaQeTOZ/3/)
4. SVN 版本地址：[http://svn1.360buy-develop.com/arch/fe/product/modules/trunk/app/js/plugins/jQuery.Jcal.js](http://svn1.360buy-develop.com/arch/fe/product/modules/trunk/app/js/plugins/jQuery.Jcal.js)

## 一、HTML 结构规范
```html
<input type="text" />
```

## 二、jQuery 初始化
```javascript
$('input').Jcal({
    chosendate: '9/9/2010',
    startdate: '6/10/2008',
    enddate: '7/20/2021',
    outputFormat: '{y}-{m}-{d}',
    onSelected: function(res) {},
    x: 0,
    y: 0
});
```

## 三、插件工作原理
查找元素绑定点击事件弹出日历

## 四、参数详情
* chosendate —— 默认选中时间
* startdate  —— 日历开始时间
* oTenddate —— 日历结束时间
* wrapClass —— 包裹元素 class
* outputFormat —— 日历输出格式
* onSelected —— 选中回调
* x —— 水平偏移量
* y —— 垂直偏移量

## 五、需要注意的几点
1. 无
