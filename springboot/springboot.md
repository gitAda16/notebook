### SpringBoot的核心功能

- 起步依赖

- 自动配置



### 特点

1 简化配置

2 下一代框架

3 入门级微框架 springCloud 微服务

```
@SpringBootApplication 程序入口
SpringApplication.run(LuckymoneyApplication.class, args);
```

### 启动方式

1 idea运行

2 mvn spring-boot:run

3 mvn clean package 打包，然后使用java -jar命令 启动

### 项目配置

application.properties

application.yml 推荐使用yml

在yml中使用配置

@Value

@Component

@Configuration

多环境配置 spring.profiles.active

### Controller的使用

@Controller 处理http请求

@RestController 原来需要使用ResponseBody配合Controller

@RequestMapping

@GetMapping 中可以放数组 可以映射多个地址

@PostMapping

PathVariable

RequestParam

### Spring-Data-Jpa

插入数据库中文字段报错

java.sql.SQLException: Incorrect string value: '\xE5\xB0\x8F\xE6\xB4\x81' for column 'producer' at row 1

首先检查mysql的字符编码，

然后连接字符串后加上编码url: jdbc:mysql://127.0.0.1:3306/lukymoney?useUnicode=true&characterEncoding=utf-8

检查表的编码

`show create table luckymoney;`

![1576594825523](C:\Users\ada\AppData\Roaming\Typora\typora-user-images\1576594825523.png)

修改表编码

`alter table luckymoney convert to character set utf8;`

数据库事务 @Transactional org.springframework.transaction.annotation.Transactional;

mysql表的引擎与事务