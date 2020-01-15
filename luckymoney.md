# Luckymoney项目

## 第四课 配置文件

```bash
# 在resource->application.xml文件中进行配置
spring.banner.charset=UTF-8    # 修改字符编码
server.port=     # 修改端口
server.servlet.context-path=/pathname   # 修改路径

# 使用开发模式和产品模式，打包后转换模式
java -jar -Dspring.profiles.active=prod/target/luckymoney-0.0.1-SNAPSHOT.jar
```

### 总结

* @Value——单个配置
* @Component
* @ConfigurationProperties——对象配置
* 多环境配置（dev/prod）

***

## 第五课 Controller的使用

* Controller：处理http请求
* RestController：Spring4之后新加的注解，原来返回json需要@ResponseBody配合@Controller
* RequestMapping（旧版）：配置URL映射

```bash
# @Controller + @ResponseBody = @RestController
# @ResponseBody可以放到方法上使用

# 多方法时可将父路径放置RequestMapping（）内
@RequestMapping("/hello")

@GetMapping("/say")   # GET请求
@PostMapping("/say")   # POST请求
@RequestMapping("/say")   #GET、POST请求皆可，但二者实现机制不同，所以最好具体使用
```

* @PathVariable：获取URL中的数据
* @RequestParam：获取请求参数的值

```bash
# @PathVariable
    @GetMapping("/say/{id}")
    public String say(@PathVariable("id") Integer id){
        return "id:" + id;
}
# http://localhost:8081/luckymoney/hello/say/100


# @RequestParam
    @GetMapping("/say")
    public String say(@RequestParam("id") Integer id){
        return "id:" + id;
}   
# 此处“@RequestParam("id")”中的id要与 “http://localhost:8081/luckymoney/hello/say?id=100” 中的id保持一致；而“Integer id”中的id与return中的id保持一致


# Other
    @GetMapping("/say")
    public String say(@RequestParam(value = "id",required = false,defaultValue="0") Integer id){
        return "id:" + id;
}

    @PostMapping("/say")
    public String say(@RequestParam(value = "id",required = false,defaultValue="0") Integer id){
        return "id:" + id;
}
# 建议在body中传参数
```

***

## 第六课 数据库

* JAP（Java Persistence API）定义了一系列对象持久化的标准，目前实现这一规范的产品有Hibernate、TopLink等。
* RESTful API设计
  1. 请求类型：GET；请求路径：/luckymoneys；功能：获取红包列表
  2. 请求类型：POST；请求路径：/luckymoneys；功能：创建一个红包
  3. 请求类型：GET；请求路径：/luckymoneys/id；功能：通过id查询红包
  4. 请求类型：PUT；请求路径：/luckymoneys/id；功能：通过id更新红包

```bash
# 配置文件配置连接数据库
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.datasource.url=jdbc:mysql://118.24.124.139:33061/luckymoney
spring.datasource.username=shu
spring.datasource.password=0912sys
spring.jpa.hibernate.ddl-auto=update   # create 创建数据库；update 修改数据库
spring.jpa.show-sql=true
```

```java
/**
建表：
1.创建新类其类名即为表名
2.类中定义变量即表中字段
3.配置文件中设置“spring.jpa.hibernate.ddl-auto=create”
4.启动项目
*/

/**
红包功能实现：
注：1.从数据库查数据需调用接口，即查询数据库数据是通过id查询实现
   2.在主类中调用接口
*/

/**
     * 1.获取红包列表
     */
@GetMapping("/luckymoneys")
    public List<Luckymoney> list(){
        return repository.findAll();
    }

/**
     * 2.创建红包
     */
    @PostMapping("/luckymoneys")
    public Luckymoney create(@RequestParam("producer") String producer, @RequestParam("money")BigDecimal money){
        Luckymoney luckymoney=new Luckymoney();
        luckymoney.setProducer(producer);
        luckymoney.setMoney(money);
        return repository.save(luckymoney);
    }

    /**
     * 3.通过id查询红包
     */
    @GetMapping("/luckymoneys/{id}")
    public Luckymoney findById(@PathVariable("id") Integer id){
        return repository.findById(id).orElse(null);
    }

    /**
     * 4.更新红包（领红包）
     */
    @PutMapping("/luckymoneys/{id}")
    public Luckymoney update(@PathVariable("id")Integer id,@RequestParam("consumer") String consumer){
        Optional<Luckymoney> optional=repository.findById(id);
        if(optional.isPresent()){
            Luckymoney luckymoney=optional.get();
            luckymoney.setConsumer(consumer);
            return repository.save(luckymoney);
        }
        return null;
    }
```

***

## 第七课 事务

* 事务处理一般放在Service里
* @Transaction添加事务