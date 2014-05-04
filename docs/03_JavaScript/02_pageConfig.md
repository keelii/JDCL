# 公共脚本中 pageConfig 详解

#### 1. wideVersion 宽窄版
一般判断页面宽窄版的时候要加上页面参数逻辑，即 `pageConfig.wideVersion&&pageConfig.compatible`
```javascript
// 源码
pageConfig.wideVersion=(function(){
    return (screen.width>=1210)
})();
```
#### 2. FN_getDomain 获取当前域名
```javascript
// 源码
pageConfig.FN_getDomain = function() {
    var hn = location.hostname;

    return (/360buy.com/.test(hn)) ? "360buy.com" : "jd.com";
};
```
#### 3. FN_GetUrl 按类型生成商品url
```javascript
// 源码
pageConfig.FN_GetUrl=function(type,skuid){
    if(typeof type=="string"){
        return type;
    }else{
        return pageConfig.FN_GetDomain(type)+skuid+".html";
    }
};
// 示例
pageConfig.FN_GetUrl(1, 676676)     // return http://item.jd.com/676676.html
pageConfig.FN_GetUrl(2, 676676)     // return http://book.jd.com/676676.html
pageConfig.FN_GetUrl(3, 676676)     // return http://mvd.jd.com/676676.html
pageConfig.FN_GetUrl(4, 676676)     // return http://e.jd.com/676676.html
```
#### 4. FN_GetImageDomain 按sku生成域名
skuid 除 5 求余即得到 sku 对应的图片域名
```javascript
// 源码
pageConfig.FN_GetImageDomain=function(a) {
    var b, a = String(a);
    switch (a.match(/(\d)$/)[1] % 5) {
    case 0:
        b = 10;
        break;
    case 1:
        b = 11;
        break;
    case 2:
        b = 12;
        break;
    case 3:
        b = 13;
        break;
    case 4:
        b = 14;
        break;
    default:
        b = 10;
    }
    return "http://img{0}.360buyimg.com/".replace("{0}", b);
};
// 示例
pageConfig.FN_GetImageDomain(676676)      // return http://img11.360buyimg.com/
```
#### 5. FN_ImgError 图片onerror
通常在动态渲染过页面后需要重新调用
```javascript
// 源码
pageConfig.FN_ImgError=function(obj){
    var imgs=obj.getElementsByTagName("img");
    for(var i=0;i<imgs.length;i++){
        imgs[i].onerror=function(){
            var css="",
                type=this.getAttribute("data-img");
            if(!type){
                return;
            }
            switch(type){
                case "1":
                    css="err-product";
                    break;
                case "2":
                    css="err-poster";
                    break;
                case "3":
                    css="err-price";
                    break;
                default:
                    return;
            }
            this.src="http://misc.360buyimg.com/lib/img/e/blank.gif";
            this.className=css;
        }
    }
};
// 示例
pageConfig.FN_ImgError(document);
```

#### 6. FN_GetCompatibleData 根据屏幕分辨率返回对象
通常用在广告位模板代码里面
```javascript
// 源码
pageConfig.FN_GetCompatibleData=function(object){
    var flag=(screen.width<1210);
    if(flag){
        object.width=object.widthB?object.widthB:object.width;
        object.height=object.heightB?object.heightB:object.height;
        object.src=object.srcB?object.srcB:object.src;
    }
    return object
};
```
