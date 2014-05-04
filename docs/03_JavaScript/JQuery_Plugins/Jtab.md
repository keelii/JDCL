## 零、插件简介
1. 插件名称：**Jtab**
2. 依赖 jQuery 版本：`1.2.6`
3. 预览地址：[jsBin](http://jsbin.com/oxogit/5/), [cssdeck](http://cssdeck.com/labs/full/bhnzsdmp)
4. SVN 版本地址：

## 一、HTML 结构规范
Tab 头与内容分离
```html
<div id="tab" class="Jtab" data-widget="tabs">
    <ul>
        <li data-widget="tab-item" class="curr">选项卡 A</li>
        <li data-widget="tab-item">选项卡 B</li>
        <li data-widget="tab-item">选项卡 C</li>
    </ul>
    <div data-widget="tab-content">选项卡 - 内容 A</div>
    <div data-widget="tab-content" class="hide">选项卡 - 内容 B</div>
    <div data-widget="tab-content" class="hide">选项卡 - 内容 C</div>
</div>
```
Tab 头与内容一体
<div id="tab2" class="Jtab" data-widget="tabs">
    <div data-widget="tab-item">
        <div class="mt">选项卡 A</div>
        <div data-widget="tab-content" class="mc">选项卡 A</div>
    </div>
    <div data-widget="tab-item">
        <div class="mt">选项卡 B</div>
        <div data-widget="tab-content" class="mc">选项卡 B</div>
    </div>
    <div data-widget="tab-item">
        <div class="mt">选项卡 C</div>
        <div data-widget="tab-content" class="mc">选项卡 C</div>
    </div>
</div> 

## 二、标题
javascript 代码示例
```javascript
$('#xx').plugin({
  //...
}});
```

## 三、标题
段落文字

## 四、标题
* 无序列表项
* 无序列表项
* 无序列表项
* 无序列表项
* 无序列表项
* 无序列表项
* 无序列表项

## 五、标题
1. 有序列表
2. 有序列表
3. 有序列表