# Qutu项目总录

## 数据库建表

1. users.Table（用户信息表）

   |   字段名   |  数据类型   | 主键 |
   | :--------: | :---------: | :--: |
   |     id     |     int     |  √   |
   |  username  | varchar(50) |      |
   |  password  | varchar(50) |      |
   |    sex     | varchar(50) |      |
   | birthdate  | varchar(50) |      |
   |    addr    | varchar(50) |      |
   | avatar_uri | varchar(50) |      |

2. favorites.Table（个人收藏表）

   |  字段名   |   数据类型   | 主键 |
   | :-------: | :----------: | :--: |
   |    id     |     int      |  √   |
   |  userid   |     int      |      |
   |  chinese  | varchar(MAX) |      |
   |  english  | varchar(MAX) |      |
   | image_uri | varchar(MAX) |      |

3. tags.Table（兴趣分类表）

   | 字段名 |  数据类型   | 主键 |
   | :----: | :---------: | :--: |
   |   id   |     int     |  √   |
   |  type  | varchar(50) |      |
   
4. searchrecords.Table（扫描记录表）

   |  字段名   |   数据类型   | 主键 |
   | :-------: | :----------: | :--: |
   |    id     |     int      |  √   |
   |  userid   |     int      |      |
   |  english  | varchar(MAX) |      |
   |  chinese  | varchar(MAX) |      |
   | image_uri | varchar(MAX) |      |
   |  typeid   |     int      |      |

5. articles.Table（文章更新表）

   | 字段名  |   数据类型   | 主键 |
   | :-----: | :----------: | :--: |
   |   id    |     int      |  √   |
   | typeid  |     int      |      |
   |  title  | varchar(50)  |      |
   | content | varchar(MAX) |      |

6. studyrecords.Table（学习记录表）

   |   字段名   | 数据类型 | 主键 |
   | :--------: | :------: | :--: |
   |     id     |   int    |  √   |
   |   userid   |   int    |      |
   | statistics |   int    |      |


## 阶段总结（2020.02.07）

### 已完成：

1. 基础环境已经搭建好，规范和公共模块制定开发完成
2. 部分静态页面已完成
3. 数据库设计完成

### 正在进行：

1. 学习Android前端布局和springboot后端开发
2. 客户端数据请求公共模块的开发，学习具体业务的写法

## 开发所遇问题

### 一、维持APP用户登录状态

![Image 2](.\picture\Image 2.png)

Token运行机制：

[1. 登录验证](https://blog.csdn.net/weixin_43495390/article/details/89278834)

### 二、单词卡片

[单词卡片](https://github.com/kikoso/Swipeable-Cards)