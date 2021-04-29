## Typora配置OSS图床

使用Typora创建markdown笔记时，图片存放位置是一个痛点。放在本地在笔记转移或发布在博客平台时会有图片路径问题，需要再次上传图片，苦不堪言。

因此为了实现本地md笔记一键copy到任意平台发布，可以配合阿里的OSS对象存储服务，打造个人图床。

开通阿里OSS服务并获取AccessKey

## 二、创建bucket

参考如下，其中bucket名称（这里是mcai）稍后会在typora配置中会用到

![image-20210427144031092](http://demo-gf.oss-cn-beijing.aliyuncs.com/image/image-20210427144031092.png)

## 三、Bucket域名

![image-20210427144319224](http://demo-gf.oss-cn-beijing.aliyuncs.com/image/image-20210427144319224.png)

## 四、创建图片目录

在名为demo-gf的的bucket中创建一个目录image，用于存放上传的图片

<img src="http://demo-gf.oss-cn-beijing.aliyuncs.com/image/image-20210427144717872.png" alt="image-20210427144717872" style="zoom:50%;" />

## 五、获取AccessKeyID和Secret

创建好后如下图，需要的信息有AccessKeyID和Secret（该项不要对外公开）

<img src="http://demo-gf.oss-cn-beijing.aliyuncs.com/image/image-20210427144836400.png" alt="image-20210427144836400" style="zoom:50%;" />

## 六、配置Typora上传工具PicGo

在Typora图像选项中进行如下配置（使用PicGo-Core）

<img src="http://demo-gf.oss-cn-beijing.aliyuncs.com/image/image-20210427144952183.png" alt="image-20210427144952183" style="zoom:50%;" />

然后打开配置文件，是PicGo的config.json，将如下信息覆盖，并对照上面替换为自己相关的信息

```
{
  "picBed": {
    "uploader": "aliyun",
    "aliyun": {
      "accessKeyId": "***************",
      "accessKeySecret": "*****************",
      "bucket": "demo-gf", // 存储空间名
      "area": "oss-cn-beijing", // 存储区域代号
      "path": "image/", // 自定义存储路径
      "customUrl": "http://demo-gf.oss-cn-beijing.aliyuncs.com", // 自定义域名，注意要加 http://或者 https://
      "options": "" // 针对图片的一些后缀处理参数 PicGo 2.2.0+ PicGo-Core 1.4.0+
    }
  },
  "picgoPlugins": {}
}
```

## 七、验证是否成功

在图像配置点击4 “验证图片上传选项”，出现如下提示表示配置成功。

<img src="http://demo-gf.oss-cn-beijing.aliyuncs.com/image/image-20210427145201440.png" alt="image-20210427145201440" style="zoom:50%;" />

