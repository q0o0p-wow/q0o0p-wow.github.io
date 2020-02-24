---
title: Live2D添加板娘
---

打开Git Bash

## 先下载live2d

``` bash
$ npm install --save hexo-helper-live2d

```

## 下载模型

``` bash
live2d-widget-model-z16
```

### 更多模型

``` bash
live2d-widget-model-chitose
live2d-widget-model-epsilon2_1
live2d-widget-model-gf
live2d-widget-model-haru/01 (use npm install --save live2d-widget-model-haru)
live2d-widget-model-haru/02 (use npm install --save live2d-widget-model-haru)
live2d-widget-model-haruto
live2d-widget-model-hibiki
live2d-widget-model-hijiki
live2d-widget-model-izumi
live2d-widget-model-koharu
live2d-widget-model-miku
live2d-widget-model-ni-j
live2d-widget-model-nico
live2d-widget-model-nietzsche
live2d-widget-model-nipsilon
live2d-widget-model-nito
live2d-widget-model-shizuku
live2d-widget-model-tororo
live2d-widget-model-tsumiki
live2d-widget-model-unitychan
live2d-widget-model-wanko
live2d-widget-model-z16
```

## 在根目录_config.yml配置下添加以下参数

``` bash
live2d:
  enable: true
  scriptFrom: local  #默认
  pluginRootPath: live2dw/ #插件在站点上是根目录
  pluginJsPath: lib/   #脚本文件相对于插件根目录路径
  pluginModelPath: assets/  #模型文件相对于与插件根目录路径
  tagMode: false  # 标签模式, 是否仅替换 live2d tag标签而非插入到所有页面中
  debug: false  # 调试, 是否在控制台输出日志
  model:
    use:  live2d-widget-model-z16 #live2d-widget-model-shizuku 要修改的 
  display:
    position: right    #在屏幕上显示的位置
    width: 150     #宽度
    height: 300    #高度
  mobile:  #是否用于移动端
    show: true  #手机是否显示
```

## 会换装的板娘

More info: [GitHub源码地址](https://github.com/pangao1990/pangao1990.github.io/tree/master/live2d)

解压到本地博客目录的 themes/.../source 下，修改文件夹名为 live2d-widget，修改项目中的 autoload.js 文件
将const live2d_path = "https://cdn.jsdelivr.net/gh/stevenjoezhang/live2d-widget/"; 改为

```
const live2d_path = "/live2d-widget/";
```


该项目需要 jQuery 和 font-awesome 支持。例如在 <head> 中加入：

在F:\blog\themes\hexo-theme-antiquity\layout\layout.ejs下添加代码

```
<script src="/live2d-widget/autoload.js"></script>
<script src="https://cdn.jsdelivr.net/npm/jquery/dist/jquery.min.js"></script>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/font-awesome/css/font-awesome.min.css">
```

![](代码添加地址2.png)

想修改看板娘大小、位置、格式、文本内容等，可查看并修改 waifu-tips.js 、 waifu-tips.json 和 waifu.css。

More info: [参考](https://blog.csdn.net/u011236348/article/details/88169549)