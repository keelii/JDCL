## 商品图片对应尺寸

标准图片：`图片域名` n `x` / `相对路径.jpg`
图片示例：`http://img10.360buyimg.com/` n `0` `/g14/M02/06/04/rBEhVlHo2EAIAAAAAANxvgFg0SkAABMqAJKaFwAA3HW057.jpg` [示例](http://img10.360buyimg.com/n0/g14/M02/06/04/rBEhVlHo2EAIAAAAAANxvgFg0SkAABMqAJKaFwAA3HW057.jpg)

`图片域名` 调用 base.js 里面的公共方法 pageConfig.FN_GetImageDomain(skuid) 会返回图片域名;

`x`           |  尺寸         |  用处
------------- | ------------- | -------------
0             |  800*800      |  原图
1             |  350*350      |  商品页主图
2             |  160*160      |  商品列表图
3             |  130*130      |  商品列表图
4             |  100*100      |  商品列表图
5             |  50*50        |  商品页主图缩略图
6             |  240*240      |
7             |  220*220      |
8             |  220*282      |  服装长图
9             |  25*25        |  列表服装缩略图

示例代码：

    var img = pageConfig.FN_GetImageDomain(1038723130) + 'n0' + '/g15/M06/14/18/rBEhWlJ8ynYIAAAAAAEKXuW3mxUAAFMHAGbk7YAAQp2959.jpg'


