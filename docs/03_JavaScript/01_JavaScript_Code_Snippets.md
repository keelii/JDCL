# 常用 JavaScript 代码片段

#### 0. 常用正规表达式

Email：/^([a-zA-Z0-9_.-])+@(([a-zA-Z0-9-])+.)+([a-zA-Z0-9]{2,4})+$/
HTML 标签：/^<([a-z]+)\s*\/?>.*(?:<\/\1>)?$/i

#### 1. 打乱数组取出 n 个 - 用于随机取数据
```javascript
function randArray(arr, len) {
    arr.sort(function () {
        return Math.random() - 0.5;
    });
    return arr.slice(0, len);
}
```

#### 2. 格式化秒数为「天、时、分、秒」 - 用户倒计时
```javascript
function formatSeconds(seconds) {

    var days = Math.floor(seconds / 86400);
    var hours = Math.floor((seconds % 86400) / 3600);
    var minutes = Math.floor(((seconds % 86400) % 3600) / 60);
    var seconds = ((seconds % 86400) % 3600) % 60;

    return {
        d: days,
        h: hours,
        m: minutes,
        s: seconds
    };
}
```
#### 3. 从脚本中插入/加载样式表
```javascript
function insertStyles(cssString) {
    var doc = document,
        heads = doc.getElementsByTagName("head"),
        style = doc.createElement("style"),
        link = doc.createElement("link");

    if ( /\.css$/.test(cssString) ) {
        link.rel = 'stylesheet';
        link.type = 'text/css';
        link.href = cssString;

        if (heads.length) {
            heads[0].appendChild(link);
        } else {
            doc.documentElement.appendChild(link);
        }
    } else {
        style.setAttribute("type", "text/css");

        if (style.styleSheet) {
            style.styleSheet.cssText = cssString;
        } else {
            var cssText = doc.createTextNode(cssString);
            style.appendChild(cssText);
        }

        if (heads.length) {
            heads[0].appendChild(style);
        }
    }
};
```
#### 4. 将参数转换成一个数组
```javascript
function Sandbox() {
    // 装参数转换成数组
    var args = Array.prototype.slice.call(arguments);
    // 传n个参数只让最后一个是回调
    var callback = args.pop();
}
```
#### 5. 对象继承「浅复制」
```javascript
function extend(parent, child) {
    var i;
    child = child || {};

    for(i in parent) {
        if (parent.hasOwnProperty(i)) {
            child[i] = parent[i];
        }
    }
    return child;
}
```
#### 5.1 对象继承「深复制」
```javascript
function extendDeep(parent, child) {
    var i,
        toStr = Object.prototype.toString,
        arrStr = '[object Array]';

    child = child || {};

    for (i in parent) {
        if (parent.hasOwnProperty(i)) {
            // 如果对象字段是 数组 或者 对象，进行递归深复制，否则浅复制
            if (typeof parent[i] === 'object') {
                child[i] = (toStr.call(parent[i]) === arrStr) ? [] : {};
                extendDeep(parent[i], child[i]);
            } else {
                child[i] = parent[i];
            }
        }
    }
    return child;
}
```
#### 6. 数字补零
```javascript
function prefixInteger(num, length) {
    return (num / Math.pow(10, length)).toFixed(length).substr(2);
}

prefixInteger(123, 4)   // "0123"
```

#### 7. JavaScript 模拟 Java hashCode 方法
```javascript
pageConfig.getHashProbability = function(strNum, baseNum) {
    // hash算法
    function hashCode(str) {
        for (var result = 0, i = 0; i < str.length; i++) {
            result = (result << 5) - result + str.charCodeAt(i);
            result &= result;
        }
        return result;
    }
    return Math.abs(hashCode(strNum)) % baseNum;
};
```