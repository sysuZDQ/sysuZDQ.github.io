# 使用GithubPage搭建个人网站
由于个人有将自己所学内容整理归档的需求，所以这里随便介绍一下使用GithubPage搭建个人网站的方法

## 创建Github仓库
该仓库的名字需要固定，即```username.github.io```。一个存放博客文档的


## 选择主题
这里我是直接使用githubpage本身支持的[主题](https://pages.github.com/themes/)，具体来说，就是fork一个主题仓库，然后将其解压到自己刚才创建的仓库中。只需要创建一个```_post```文件夹存放自己的文章，我这里使用的是md文件。然后在index.md（这是网站入门的文件）中引用该文件即可。值得注意的是，在引用的时候需要将后缀从```md```改为```html```

## 更多主题
- https://zhuanlan.zhihu.com/p/51240503
- https://jekyllcn.com/
- https://zhuanlan.zhihu.com/p/87225594


## 博客搭建方式
https://www.yuque.com/bithachi/study/cb2rud
[网站主机教程](https://www.runoob.com/hosting/hosting-tutorial.html)
### 动态
如**WordPress**，因为博客文章、图片、评论、分类和标签等数据都是从数据库里面拿出来的，不是死的，是活的。WordPress搭建挺方便的，只要有个服务器和域名就行，评论和SEO都不用你操心，可以在后台安装一些插件，对博客网站进行扩展，比如WordPress不是原生支持markdown语法的，就可以安装插件，实现markdown的渲染，包括代码块的显示等。
### 静态
**Hexo**不需要很多的维护费用，但是搭建Hexo需要使用git（vscode有插件支持图形化命令）然后就是需要node.js去渲染你的博客，渲染完把代码推送到代码托管平台，这里也就是Hexo的静态性了，Hexo的博客内容不是从数据库里面拿出来的，它是根据你的markdown文档加博客主题通过node.js来渲染你的代码，直接将文章与html等前端代码嵌在一起，就像访问静态网站一样。如果你想要评论功能，SEO让搜索引擎收录你的文章。