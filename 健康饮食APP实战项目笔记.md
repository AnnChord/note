# 健康饮食APP实战项目笔记

## 视频2：ListView的应用

注：首先引入数据源，并对数据源进行封装，用List数组循环存储数据源

1. 在主界面的xml文件中引入ListView控件，并对相关属性进行设置（总）
2. 新建item_searchlist_lv.xml文件，在该文件中设计ListView样式（个体）
3. 新建适配器，创建SearchListAdapter.java文件，在文件中写入相关item_searchlist_lv.xml中控件和数据源的绑定
4. 在主界面中调用适配器

## 视频3：GridView的应用

1. Serializable：传递序列化类型



## 视频4：ViewPager的应用

* 布局：

  1、ImageView：scaleType=“centerCrop”    等比例放大

**自动无限播放页面：**

1. 无限：更改Adapter里的配置
2. 自动：在Activity里加入handller计时器

## 语法缩写

```java
fori       //打出for循环
创建适配器new Adapter（）.field;     //定义适配器     
```

