项目初始配置

建表

pom配置：

mybatis配置

mysql驱动

数据库连接池

mapper可以有工具自动化生成

了解mybatis的配置

编写测试类 使用两个注解

```
@RunWith(SpringRunner.class)
@SpringBootTest
```

 遇到mysql无法启动的情况，没有报错，可以在我的电脑--右键管理--

![1576895958194](C:\Users\ada\AppData\Roaming\Typora\typora-user-images\1576895958194.png)

``` 
PathMatchingResourcePatternResolver getResource getResouces两个好像不一样 有s的会抛出ioexception，没s的好像没法解析classpath
```

了解@Transactional

```
了解@RequestBody
```

统一异常处理@ControllerAdvice

微信小程序文档 报读，查看帮助文档

一定要项目设置勾选不校验http证书

小程序有个奇怪的地方，调试的时候，在watch输入变量，来观察变量值，如果变量是在函数外定义的，但是函数内没有使用到该变量，当程序运行到函数内部是，此时调试中watch这个变量，显示是unavailabel



如果希望在开发的控制台打印日志，设置logging:  level:    root: debug