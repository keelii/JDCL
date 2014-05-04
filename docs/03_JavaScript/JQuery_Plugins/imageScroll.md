# 图片滚动
## 零、插件简介
1. 插件名称：**imgScroll**
2. 依赖 jQuery 版本：`1.2.6`
3. 预览地址：[jsFiddle](http://jsfiddle.net/keelii/b4EuV/), [jsBin](http://jsbin.com/ecunum/9/)
4. SVN 版本地址：[http://svn1.360buy-develop.com/arch/f2e/source/trunk/360buy/common/components/imageScroll](http://svn1.360buy-develop.com/arch/f2e/source/trunk/360buy/common/components/imageScroll)

## 一、HTML 结构规范
```html
<div id="xx">
  <ul>
    <li><img src="test.jpg" /></li>
    <li><img src="test1.jpg" /></li>
    <li><img src="test2.jpg" /></li>
  </ul>
</div>
<div>
  <span id="prev"><</span>
  <span id="next">></span>
</div>
```

## 二、jQuery 初始化
```javascript
$('#xx').imgScroll({
  visible: 3,
  step: 1,
  next: '#next',
  prev: '#prev'
});
```

## 三、插件工作原理
插件初始化后会按照传入的jQuery选择器(#xx)元素为始，寻找子元素下所有的 li 元素标 签，并记录 li 元素的高、宽参数备用。按时设置的参数计算出应该显示出来的 li 标签个数， 并将(#xx)元素样式重置为相对定位，子元素 ul 设置绝对定位并且设置宽度。

## 四、参数详情
* visible —— 可视滚动数 默认值：3
* speed —— 滚动速度 默认值：300
* step —— 每次滚动个数 默认值：1
* loop —— 是否循环滚动，布尔值true or false 默认值：false
* next, prev —— 下一张、上一张按钮选择器，比如：.prev, #next 默认值：.next,.prev
* disableClass —— 滚动到头\无法滚动时按钮添加的class 默认值：disabled
* evtType —— 事件触发类型，比如：click，mouseover 默认值：click

## 五、需要注意的几点
1. 控制按钮和滚动图片没有嵌套关系，按钮可以是页面上的任意元素，建议用id选择器传入按钮参数
2. 不要给 li 标签加外间距margin\border，会影响计算精度，必须要加的话可以给li内嵌套其它元素添加间距
3. 当出现一些错误弹出框时请检查参数visible\step和li元素个数的对应关系，是否满足滚动的条件。比如：当step值大于visible的时候就会丢掉某个滚动元素。类似情况会alert提示
