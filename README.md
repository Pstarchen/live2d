# KanBanMusume
WordPress添加看板娘

# 看板娘简介

看板娘就是一个卡通模型，通过代码的部署，会在你网页的指定位置进行显示，你用鼠标进行点击会有不同地字幕，所有的一切都可以预先进行设置。

# 代码地址
 [Pstarchen/live2d: live2d看板娘](https://github.com/Pstarchen/live2d)

# 设置教程
下载文件后解压代码到你的博客网站根目录去。（目录位置可以自定义）
然后把解压出来的文件夹改名为：live2d 。
在博客程序头部文件（header.php）引入界面样式，在 head 标签内插入如下代码
```
<link rel="stylesheet" href="/live2d/css/live2d.css" />
```

在你博客程序页脚文件（footer.php）引入脚本，在最后一个 head 标签前插入如下代码：
```
<div id="landlord">
    <div class="message" style="opacity:0"></div>
    <canvas id="live2d" width="280" height="360" class="live2d"></canvas>
</div>
 

<script type="text/javascript">
    var message_Path = '/live2d/'
    var home_Path = 'https://www.kxceping.com/'  //此处修改为你的域名，必须带斜杠
</script>
<script type="text/javascript" src="/live2d/js/live2d.js"></script>
<script type="text/javascript" src="/live2d/js/message.js"></script>
<script type="text/javascript">
    loadlive2d("live2d", "/live2d/model/tia/model.json");
</script>
```
鼠标放在页面某个元素上时，需要 Live2D 看板娘提示的请修改 message.json 文件。

实例：
```
{
    "mouseover": [
        {
            "selector": ".title a",  //此处修改为你页面元素的标签名
            "text": ["要看看 {text} 么？"]  //此处修改为你需要提示的文字
        },
        {
            "selector": "#searchbox",
            "text": ["在找什么东西呢，需要帮忙吗？"]
        }
    ],
    "click": [  //此处是 Live2D 看板娘的触摸事件提示
        {
            "selector": "#landlord #live2d",
            "text": ["不要动手动脚的！快把手拿开~~", "真…真的是不知羞耻！","Hentai！", "再摸的话我可要报警了！⌇●﹏●⌇", "110吗，这里有个变态一直在摸我(ó﹏ò｡)"]
        }
    ]
}
```

清除浏览器缓存，刷新，看看效果吧。

# 修改配置
如果需要修改看板娘的位置，只需要进入根目录./live2d/css/live2d.css，修改内容。
如要将看板娘从左边移到右边，只需将
```
#landlord {
    user-select: none;
    position: fixed;
    left: 5px;
    bottom: 0;
    width: 280px;
    height: 250px;
    z-index: 10000;
    font-size: 0;
    transition: all .3s ease-in-out;
}
```
其中的left改为right即可。
最后别忘了清理浏览器缓存哦！
