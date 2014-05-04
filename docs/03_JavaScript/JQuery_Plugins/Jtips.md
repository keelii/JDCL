# 提示信息
## 零、插件简介
1. 插件名称：**Jtips**
2. 依赖 jQuery 版本：`1.2.6`
3. 预览地址：[jsFiddle](http://jsfiddle.net/keelii/8kszP/), [jsBin](http://jsbin.com/ikezuk/4/)
4. SVN 版本地址：

## 一、HTML 结构规范
```html
<a id="tp" class="Jtips">这是个普通链接</a>
```

## 二、jQuery 初始化
```javascript
$('#tp').Jtips({
});
```

## 三、插件工作原理
插件根据传入 jQuery 对象生成一个元素并定位到元素周围（上下左右），可以关闭、显示、隐藏等

## 四、参数详情
* content —— Tips 内容 默认是标签的 title 属性
* width —— 宽度
* oTop —— 垂直偏移量
* oLeft —— 水平偏移量
* zIndex —— 层级值
* event —— Tips 显示触发事件，默认直接显示
* position —— 位置，默认`top`
* close —— 关闭按钮

## 五、需要注意的几点
1. 插件 `width` 参数必须设置，否则无法定位
