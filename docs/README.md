## 首页

E-mail: 1335680234@qq.com

[Github](<https://github.com/wfy-belief>)



## 可视化展示



```chart
{
    color: ['#3398DB'],
    tooltip: {
        trigger: 'axis',
        axisPointer: {            // 坐标轴指示器，坐标轴触发有效
            type: 'shadow'        // 默认为直线，可选为：'line' | 'shadow'
        }
    },
    grid: {
        left: '3%',
        right: '4%',
        bottom: '3%',
        containLabel: true
    },
    xAxis: [
        {
            type: 'category',
            data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
            axisTick: {
                alignWithLabel: true
            }
        }
    ],
    yAxis: [
        {
            type: 'value'
        }
    ],
    series: [
        {
            name: '直接访问',
            type: 'bar',
            barWidth: '60%',
            data: [10, 52, 200, 334, 390, 330, 220]
        }
    ]
};

```



## 可视化展示2




```chart
{"backgroundColor":"#0f375f","tooltip":{"trigger":"axis","axisPointer":{"type":"shadow"}},"legend":{"data":["line","bar"],"textStyle":{"color":"#ccc"}},"xAxis":{"data":["2020-8-6","2020-8-7","2020-8-8","2020-8-9","2020-8-10","2020-8-11","2020-8-12","2020-8-13","2020-8-14","2020-8-15","2020-8-16","2020-8-17","2020-8-18","2020-8-19","2020-8-20","2020-8-21","2020-8-22","2020-8-23","2020-8-24","2020-8-25"],"axisLine":{"lineStyle":{"color":"#ccc"}}},"yAxis":{"splitLine":{"show":false},"axisLine":{"lineStyle":{"color":"#ccc"}}},"series":[{"name":"line","type":"line","smooth":true,"showAllSymbol":true,"symbol":"emptyCircle","symbolSize":15,"data":[198.942212563156,366.8060699512149,196.48967479337725,24.29298675810525,168.0338457269178,153.5156766806652,223.4195712611015,181.6460561593846,213.45620369147406,82.00441926151765,157.38645624463098,183.16585974533535,239.93047972498016,179.88631616746625,123.39764182675036,113.29055089043462,280.8749699195737,325.44613516324455,176.2889275563062,69.11124457501114]},{"name":"bar","type":"bar","barWidth":10,"itemStyle":{"barBorderRadius":5,"color":{"x":0,"y":0,"x2":0,"y2":1,"type":"linear","global":false,"colorStops":[{"offset":0,"color":"#14c8d4"},{"offset":1,"color":"#43eec6"}]}},"data":[97.88187483052462,194.49269817041207,36.21757125044858,0.45554376375225303,131.02762043759824,22.75921309225599,42.58443238130387,140.9373854855118,148.98963559302598,59.79003018838185,153.09649883939764,157.64904164280122,154.48031843379954,150.11893296432376,119.31654201071376,6.402649516036796,94.86033856249989,154.7511176577258,124.59229259544351,51.35249168772948]},{"name":"line","type":"bar","barGap":"-100%","barWidth":10,"itemStyle":{"color":{"x":0,"y":0,"x2":0,"y2":1,"type":"linear","global":false,"colorStops":[{"offset":0,"color":"rgba(20,200,212,0.5)"},{"offset":0.2,"color":"rgba(20,200,212,0.2)"},{"offset":1,"color":"rgba(20,200,212,0)"}]}},"z":-12,"data":[198.942212563156,366.8060699512149,196.48967479337725,24.29298675810525,168.0338457269178,153.5156766806652,223.4195712611015,181.6460561593846,213.45620369147406,82.00441926151765,157.38645624463098,183.16585974533535,239.93047972498016,179.88631616746625,123.39764182675036,113.29055089043462,280.8749699195737,325.44613516324455,176.2889275563062,69.11124457501114]},{"name":"dotted","type":"pictorialBar","symbol":"rect","itemStyle":{"color":"#0f375f"},"symbolRepeat":true,"symbolSize":[12,4],"symbolMargin":1,"z":-10,"data":[198.942212563156,366.8060699512149,196.48967479337725,24.29298675810525,168.0338457269178,153.5156766806652,223.4195712611015,181.6460561593846,213.45620369147406,82.00441926151765,157.38645624463098,183.16585974533535,239.93047972498016,179.88631616746625,123.39764182675036,113.29055089043462,280.8749699195737,325.44613516324455,176.2889275563062,69.11124457501114]}]}
```



## 可视化展示3



```chart
{"tooltip":{"trigger":"item","formatter":"{a} <br/>{b}: {c} ({d}%)"},"legend":{"orient":"vertical","left":10,"data":["直达","营销广告","搜索引擎","邮件营销","联盟广告","视频广告","百度","谷歌","必应","其他"]},"series":[{"name":"访问来源","type":"pie","selectedMode":"single","radius":[0,"30%"],"label":{"position":"inner"},"labelLine":{"show":false},"data":[{"value":335,"name":"直达","selected":true},{"value":679,"name":"营销广告"},{"value":1548,"name":"搜索引擎"}]},{"name":"访问来源","type":"pie","radius":["40%","55%"],"label":{"formatter":"{a|{a}}{abg|}\n{hr|}\n  {b|{b}：}{c}  {per|{d}%}  ","backgroundColor":"#eee","borderColor":"#aaa","borderWidth":1,"borderRadius":4,"rich":{"a":{"color":"#999","lineHeight":22,"align":"center"},"hr":{"borderColor":"#aaa","width":"100%","borderWidth":0.5,"height":0},"b":{"fontSize":16,"lineHeight":33},"per":{"color":"#eee","backgroundColor":"#334455","padding":[2,4],"borderRadius":2}}},"data":[{"value":335,"name":"直达"},{"value":310,"name":"邮件营销"},{"value":234,"name":"联盟广告"},{"value":135,"name":"视频广告"},{"value":1048,"name":"百度"},{"value":251,"name":"谷歌"},{"value":147,"name":"必应"},{"value":102,"name":"其他"}]}]}
```



## 构建方法

1. 初始化仓库

   ```
   git  init
   ```

2. 于远程仓库建立连接

   ```
   git remote add origin https://github.com/wfy-belief/python.git
   ```

3. 拉取远程主分支

   ```
   git pull origin master
   ```

4. 推送到远程分支

   ```
   git push -u origin master
   ```

这样就与远程仓库建立了连接就可以用Git提交代码了

```
git add .     //将代码放到缓存区
git commit -m""   //提交到本地仓库
git push          //推送到远程
```

## 