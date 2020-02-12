# Android基础知识学习

## 一、Android当中数据存储的方式

1. ShardPreference   共享参数
2. File存储：内部存储，外部存储（SDCard存储）
3. SQLLite数据库存储
4. Content Proivder    内容提供者
5. 网络存储

### 1. ShardPreference   共享参数

#### 特征

1. 存放轻量级数据的存储方式。
2. 本质是存储为xml文件形式，然后通过读取键值对的形式对数据进行操作。
3. 通常是用于存储一些简单的配置信息。

#### 用法

**存储**

1. getSharedPreferences(String name,int mode)方法   //针对context

| parameters ： |                  |
| :-----------: | :--------------: |
|     name      | 所存配置文件名称 |
|     mode      |       权限       |

mode：

MODE_PRIVATE                        ：只能被本程序读写

Mode_WORLD_READABLE      ：已生成的xml文件可以在其他程序中可读

MODE_WORLD_WRITEABLE    ： 已生成的xml文件可以在其他程序中可写

MODE_MULTI_PROCESS          ： 更改数据时提醒的进程

2. 存放数据的方法用SharedPreferences.Editor

![image-20200209231105363](C:\Users\anne\AppData\Roaming\Typora\typora-user-images\image-20200209231105363.png)

**读取**

ShardPreference方法：

![image-20200210121716971](C:\Users\anne\AppData\Roaming\Typora\typora-user-images\image-20200210121716971.png)

#### 例子

**通过共享参数来存数据步骤：**

1. 获得SharedPreference的对象，getSharedPreferences(String ,int )；
2. 获取Editor的对象，通过SharedPreference.edit()方法
3. 调用Editor对象的putxxx(key,value)的方法，来存放数据。
4. 调用editor.commit()方法，提交添加或修改的内容。

![1](C:\Users\anne\AppData\Roaming\Typora\typora-user-images\1.jpg)

![2](C:\Users\anne\AppData\Roaming\Typora\typora-user-images\2.jpg)

**共享参数取出数据的步骤：**

1. 获得SharedPreference的对象，getSharedPreferences(String ,int )；
2. 调用SharedPreference的对象中的getxxx()方法，传入相应的key值，就能获取到数据了。

![3](C:\Users\anne\AppData\Roaming\Typora\typora-user-images\3.jpg)

#### 总结

**使用共享参数存放数据的位置：**

data/data/<你的包名>/shared_prefs/...

***

editor.clear()           ：清空所有的数据内容

editor.remove(key)：移除指定键值的数据

***

sharedpreferences.contains(key)：判断数据中是否包含此键值。

***

getSharedPreferences(String ,int )；

name：生成的xml文件的名称

mode：生成文件的权限

MODE_PRIVATE、MODE_PRIVATE、MODE_WORLD_WRITEABLE、MODE_MULTI_PROCESS（如**用法**所示）

