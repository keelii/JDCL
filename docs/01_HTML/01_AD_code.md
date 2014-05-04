# 广告位代码片段

## 零、广告位调用方法
新（单个）：http://fa.360buy.com/loadFa.js?aid=`4_353_2091`
新（批量）：http://fa.360buy.com/loadFa_toJson.js?aid=`2_163_817`-`2_163_818`
老：http://www.360buy.com/hotwords.aspx?Position=`popxn_140`

## 一、广告位模板字段

1. 窄版图片：${being.imageUrl}
2. 宽版图片：${being.bigImageUrl}
4. 缩略图片：${being.smallImageUrl}
5. 链接地址：${being.href}
6. 图片说明：${being.imageAlt}
7. 扩展字段：${being.ext**n**} `n = 1~6`

## 二、常用广告位模板
#### html模板示例
此方法由开发直接读取广告位插入页面

    <#list adList as being>
        <li class="item">
            <a target="_blank" title="${being.imageAlt}" href="${being.href}">
                <img height="108" width="108" alt="${being.imageAlt}" data-lazyload="${being.bigImageUrl?trim}">
            </a>
        </li>
    </#list>

#### javascript模板示例（简单）

    <script>
        var slider_banner = [
        <#list adList as being>
        <#if being_index!=0>,</#if>
        {
            srcA: "${being.imageUrl}",
            srcB: "${being.bigImageUrl}",
            href: "${being.href}",
            alt: "${being.imageAlt}",
            bgColor: "${being.ext1}"
        }
        </#list>
        ];
    </script>

#### javascript模板示例（复杂）

    <script>
    newSlide.push({
        main: {
            <#list adList as being>
                <#if being_index==0>
                srcA: "${being.imageUrl}",
                srcB: "${being.bigImageUrl}",
                href: "${being.href}",
                alt: "${being.imageAlt}",
                bgColor: "${being.ext1}"
                </#if>
            </#list>
        },
        ext: [
            <#list adList as being>
                <#if being_index!=1&&being_index!=0>,</#if>
                <#if being_index!=0>
                    {
                        src: "${being.bigImageUrl}",
                        alt: "${being.imageAlt}",
                        href: "${being.href}"
                    }
                </#if>
            </#list>
        ]
    });
    </script>

#### 从javascript加载广告位

**广告位输出必须是javascript代码（不能有script标签）**

    $.ajax({
        url: 'http://fa.jd.com/loadFa_toJson.js?aid=2_163_817-2_163_818-2_232_3431-2_163_3743',
        dataType: 'script'
    });
