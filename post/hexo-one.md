---
title: hexo的简单使用
---
Welcome to [Hexo](https://hexo.io/)! Check [documentation](https://hexo.io/docs/) . If you get any problems when using Hexo, you can find the answer in [troubleshooting](https://hexo.io/docs/troubleshooting.html)  [GitHub](https://github.com/hexojs/hexo/issues).

## Quick Start

### Create a new post

``` bash
$ hexo new "My New Post"
```

More info: [Writing](https://hexo.io/docs/writing.html)

### Run server

``` bash
$ hexo s  //hexo server简写
```

More info: [Server](https://hexo.io/docs/server.html)

### Generate static files

``` bash
$ hexo generate
```

More info: [Generating](https://hexo.io/docs/generating.html)

### Deploy to remote sites

``` bash
$ hexo deploy
```

More info: [Deployment](https://hexo.io/docs/deployment.html)

## 安装插件

```bash
npm install https://... -- save
npm install https://github.com/CodeFalling/hexo-asset-image -- save  //例如插入图片的要安装的插件
```
设置站点配置_config.yml:将post_asset_folder: false改为post_asset_folder: true

![](代码添加地址1.png)

安装完成后，再运行hexo n “title”  source/_posts文件夹内除了title.md文件还有一个同名的文件夹

在title.md中引入图片时，先把图片复制到title这个文件夹中，然后只需要在title.md中按照markdown的格式引入图片：

! [ 你想输入的替代文字 ] ( title/图片名.jpg )

最后
```
hexo g -d同步到github
```

### 在GitHub上下载

```
 git clone https://github.com/yiluyanxia/hexo-theme-antiquity.git  //例如下载主题
```


###