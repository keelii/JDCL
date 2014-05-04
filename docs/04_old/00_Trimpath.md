# Trimpath 模板引擎使用指南

## 零、用法
1.字段调用

    ${val}

2.判断

    {if cond}
    {/if}

    {if cond}
    {else}
    {/if}

2.循环

    {for item in json}
    {/for}

    {for}
    {forelse}
    {/for}

## 一、实例
```javascript
    var json = {
        "success": true,
        "latency": 6,
        "data": [{
            "sku": 520139,
            "t": "闪迪（SanDisk）MicroSDHC（TF）存储卡 8G-Class4",
            "jp": "34.9",
            "mp": "59.0",
            "img": "2344/baa353fa-515d-48e1-816e-ed6cd7ffdf3a.jpg",
        }, {
            "sku": 1028454735,
            "t": "韩国进口Zenus三星note8.0签字皮套带支架 适用于n5100 n5110 咖啡",
            "jp": "288.0",
            "mp": "578.0",
            "img": "g15/M01/00/1B/rBEhWlHuDloIAAAAAARsSYiSJcsAABTWAPJ3cIABGxh942.jpg",
        }]
    };

    var TPL = '<ul>'
        +'  {for item in data}'
        +'  <li class="fore${Number(item_index)+1}">'
        +'      <div class="p-img">'
        +'          <a target="_blank" title="${item.t}" href="http://item.jd.com/${item.sku}.html"><img height="100" width="100" alt="${item.t}" data-lazyload="${pageConfig.FN_GetImageDomain(item.sku)}n4/${item.img}"></a>'
        +'      </div>'
        +'      <div class="p-name">'
        +'          <a target="_blank" title="${item.t}" href="http://item.jd.com/${item.sku}.html">${item.t}</a>'
        +'      </div>'
        +'      <div class="p-price">'
        +'          <strong class="J-p-${item.sku}">${item.jp}</strong>'
        +'      </div>'
        +'  </li>'
        +'  {/for}'
        +'</ul>';

    alert(TPL.process(json));
```



