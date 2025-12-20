# 中州养老项目
前端：Vue3+Element Plus
后端：若依框架，SpringBoot,Spring Security,Mybatis,Mybatis-Plus，MySQL,Redis


## Mybatis-plus学习
起步：项目导入
先打开idea的设置按钮，找到构建，执行，部署
![[Pasted image 20251220145218.png]]

检查这里的Maven版本和Java编译器版本
其次：打开项目结构
![[Pasted image 20251220145312.png]]
确保项目的SDK和模块一致，这样项目初始化算是完成了

前端项目启动：nginx
在Windows当中，nginx中的那个文件夹，路径绝对不能包含中文，否则将无法打开，nginx又是一闪而过的，所以不好排查，以后假如遇到前端需要通过nginx启动的，一定要放在非中文目录下，下面附上一张gemini的解释：
![[Pasted image 20251220150549.png]]



Mybatis-plus起步：
第一步：pom.xml导入依赖
```
<!--        Mybatis-Plus-->  
        <dependency>  
            <groupId>com.baomidou</groupId>  
            <artifactId>mybatis-plus-spring-boot3-starter</artifactId>  
            <version>3.5.11</version>  
        </dependency>
```
注意：Mybatis依赖和Mybatis-plus的依赖不能同时存在，一般项目开发都是直接导入mybatis-plus
第二步：application启动文件进行Mapper扫描，扫描相对路径
```
@MapperScan("com.xxxxx.mapper")
```
第三步：Mapper层进行继承BaseMapper,注意BaseMapper<T>这个泛型

```
public interface XxxxMapper extends BaseMapper<实体类>
```

第四步：实体类中使用注解标记主键，自增方式

第五步：impl层中使用

mybatis-plus的强大功能：
1.可以将实体类名转换成小写下划线的名字（方便和数据库进行匹配，建表的时候也推荐使用下划线方式）
2.



