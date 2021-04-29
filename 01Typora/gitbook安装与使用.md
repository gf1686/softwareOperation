# 1. Gitbook的安装

### node.js的安装

gitbook是一个基于Node.js的命令行工具，所以要先安装Node.js(下载地址：[https://nodejs.org/en/](https://links.jianshu.com/go?to=https%3A%2F%2Fnodejs.org%2Fen%2F)，找到对应平台的版本安装即可)。

Node.js都会默认安装npm（node包管理工具），所以不需要单独安装npm，打开命令行，执行以下命令安装GitBook。

```
npm install -g gitbook-cli
```

# 2. 编辑工具的安装

编辑工具使用gitbook editer和typora。

# 3. Gitbook的使用

在你想要的位置新建一个文件夹，然后打开命令行，cd到这个文件夹下。

接着执行以下命令

```shell
gitbook init
```

执行完后，文件夹里会多两个文件

README.md（书籍的介绍在这个文件里）

SUMMARY.md（书籍的目录结构在这里配置）

## 3.1 写目录

后面我介绍了一个生成目录的插件，所以不一定要自己弄目录，但这里还是说下怎么写

上面说到SUMMRAY.md文件就是整个文件夹的目录，写目录其实就是编辑这个文件，刚打开时这个文件里什么都没有，我先在给他编写一下:

![image-20210429140252036](http://demo-gf.oss-cn-beijing.aliyuncs.com/image/image-20210429140252036.png)

在给大家看看源代码:

```
# Summary

* [Introduction](README.md)
* [前言](readme.md)
* [第一章](part1/README.md)
    * [第一节](part1/1.md)
    * [第二节](part1/2.md)
    * [第三节](part1/3.md)
    * [第四节](part1/4.md)
* [第二章](part2/README.md)
* [第三章](part3/README.md)
* [第四章](part4/README.md)
```

可以复制源代码过去试一下

简单给大家说一下语法：中括号里是这个目录的名字，小括号里是路径。

写完目录后再次执行`gitbook init` Gitbook会查找SUMMARY.md中描述的目录和文件，如果没有则会创建。上面的目录运行后是这样的

<img src="http://demo-gf.oss-cn-beijing.aliyuncs.com/image/image-20210429140316212.png" alt="image-20210429140316212" style="zoom:50%;" />

## 3.2 写笔记

在这里给大家介绍一些typora比较常用的功能

## 3.3 各级标题

在typora中使用crtl + 1~6可以创建1-6级标题，1级最大，6级最小。同时typora的大纲会显示所有标题，如图：

<img src="http://demo-gf.oss-cn-beijing.aliyuncs.com/image/image-20210429140348215.png" alt="image-20210429140348215" style="zoom:50%;" />

## 3.4 表格

可以在段落--->表格中插入表格，或者按快捷键crtl+T

## 3.5 代码块

这个功能用的很频繁，可以在段落--->代码块中插入，也可以使用快捷键(```+空格)

## 3.6 专注模式和打字机模式

打字机模式就是让当前输入行保持在屏幕中间，专注模式就是输入行正常颜色，其他行变灰，可以在视图中打开

## 3.7 源代码模式

源代码模式就是展示Markdown的文件本来的样子，如图



这个模式会展示出Markdown文件的标识符

## 3.8 插入图片

这个不多说，在格式--->图像里，快捷键crtl+shift+i

## 3.9 插入链接

用两个尖括号括起来就行，如下：

<[www.baidu.com]>

## 3.10 更换主题

直接点主题就好，typora内置了6个主题，值得一提的是typora的主题是css格式，所以会css的小伙伴可以自己写主题，或者调整已有的主题

## 3.11 内容目录

就是你们在本文上面看到的那个目录，简单点说就是把大纲放到了文章里，在段落--->内容目录里可以找到（有标题时才能用）

## 3.12 常见的格式

就比如加粗，斜体，下划线什么的。在格式里有，快捷键如下：



## 3.13 我的使用方法

其实单个md文件可以存储很多笔记，我现在是把一块笔记存在一个md文件里，有一定规模后再装文件夹，然后放在gitbook中，再使用我介绍的插件生成目录。

# 4、插件的使用方法

在gitbook中有很多有用的插件，但是使用起来会有一点麻烦，这里给大家讲解一下怎么用。

gitbook的插件大部分都在npm上，可以访问npm官网查看搜索插件[https://www.npmjs.com/](https://links.jianshu.com/go?to=https%3A%2F%2Fwww.npmjs.com%2F)

这里用一个自动生成目录的插件给大家介绍使用方法

名字叫:[gitbook-plugin-summary](https://links.jianshu.com/go?to=https%3A%2F%2Fplugins.gitbook.com%2Fplugin%2Fgensum)

1. 首先打开你笔记文件夹下的book.json文件，没有就自己创建一个

2. 将以下代码复制进去

   

   ```json
   {
     "plugins": ["summary"]
   }
   ```

3. 打开命令行，在这个文件夹中执行命令`gitbook install`安装插件

4. 执行命令`gitbook serve`然后在查看的时候就会发现，之前明明没有写目录，现在却有了目录。大家想要用别的插件可以直接去npm上找，都有使用方法的

# 5、生成电子书

写完后我们可以执行`gitbook serve`来预览这本书，执行后会把Markdown格式的文档转换为html格式，最后提示"Serving book on [http://localhost:4000](https://links.jianshu.com/go?to=http%3A%2F%2Flocalhost%3A4000)"此时用浏览器打开" [http://localhost:4000](https://links.jianshu.com/go?to=http%3A%2F%2Flocalhost%3A4000)"即可预览书本

如图：

![image-20210429134534223](http://demo-gf.oss-cn-beijing.aliyuncs.com/image/image-20210429134534223.png)

执行完后你的笔记文件夹里会多一个_book文件夹，里面是转化后的html文件

# 6. 笔记的同步

## 6.1 同步单个的md文件

对于单个的md文件，我建议同步到石墨文档，可以在网页版，桌面版，移动版三个版本上查看和编辑。操作方法就是打开然后带入就行了。当然，在博客上发布也不失为一种好的同步方法。

## 6.2 同步整个笔记文件

可以使用git同步到github。

