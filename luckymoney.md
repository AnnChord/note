# Luckymoney项目

## 第四课 配置文件

```bash
#在resource->application.xml文件中进行配置
server.port=     #修改端口
server.servlet.context-path=/pathname   #修改路径

#使用开发模式和产品模式，打包后转换模式
java -jar -Dspring.profiles.active=prod/target/luckymoney-0.0.1-SNAPSHOT.jar
```

