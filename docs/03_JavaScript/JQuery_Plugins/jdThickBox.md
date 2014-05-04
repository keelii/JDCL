# 弹出层/窗口
## 零、插件简介
1. 插件名称：jdThickBox
2. 依赖 jQuery 版本：`1.2.6`
3. 预览地址：[jsBin](http://jsbin.com/yawuv/12/edit)
4. SVN 版本地址：

## 一、HTML 示例
html 代码示例

```html
<a href="#none" id="auto-pop">点我能出来弹出层</a>
```

## 二、初始化脚本
```javascript
$('#auto-pop').jdThickBox({
    width: 100px,
    height: 50px,
    source: '这是被动点击弹出的内容'
});
$('#auto-pop1').jdThickBox({
    title: '这是点击弹出的内容而且有回调',
    width: 300,
    height: 50,
    source: '这是点击弹出的内容而且有回调'
}, function() {
    alert("回调在这儿。");
});
```

## 三、参数详情
* type: "text"              > 类型
* source: null              > 弹出HTML内容
* width: null               > 高度
* height: null              > 宽度
* title: null               > 标题
* _frame: ""                > 元素id
* _div: ""                  > ...
* _box: ""                  > ...
* _con: ""                  > ...
* _loading: "thickloading"
* close: false
* _close: ""                > ...
* _fastClose: false         > 快速关闭，点击非弹出层关闭
* _close_val: "×"
* _titleOn: true
* _title: ""
* _autoReposi: false        > 自动滚动定位
* _countdown: false         > 倒计时

## 三、需要注意的地方
1. **必须**指定高度、宽度，否则无法计算初始化位置
2. 调用iframe时，iframe可调用parent.jdThickBoxclose方法关闭原层
