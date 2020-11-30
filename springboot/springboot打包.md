直接使用maven package打包即可

如何分离配置文件，就是说不把配置文件打包到jar里面,在pom里面配置

```xml
<build>
<resources>
            <resource>
                <directory>src/main/resources</directory>
                <excludes>
                    <exclude>**/application.properties</exclude>
                    <exclude>**/application.yml</exclude>
                </excludes>
            </resource>
        </resources>
    </build>
```

