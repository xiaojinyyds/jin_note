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
2.可以将实体中的列名转换为小写加下划线，并根据变量类型推断字段类型
3.mybatis-plus会把名为id的字段作为主键

有些情况下，实体中的类名和表名不完全一致，这个时候需要我们通过一些注解来声明：
1.@TableName:用来指定表名
2.@TableField:用来指定表中的普通字段信息
（1）：数据库中字段名和实体类中的字段名不匹配，所以加上TableField
（2）：数据库中的字段名和关键字重名，例如：order，这个时候需要使用TableField进行声明：
@TableField("`order`")//双引号和反引号嵌套模式
（3）：实体类中的字段存在，但是数据库中不存在，这个时候需要使用TableField进行声明：
@TableField(exist=false)

3.@TableId:用来指定表中的主键字段信息
（1）实体类名为id,数据库名不为id，就需要指定。
（2）type类型：IdType.AUTO（自增）,IdType.ASSIGN_ID（雪花算法）,IdType.ASSIGN_UUID(不推荐)


mybatis-plus在application.yml中的一些常见配置：

```
mybatis-plus:
  global-config:
    db-config:
      id-type: auto             # 全局id类型为自增长
      update-strategy: not_null # 更新策略：只更新非空字段
```

```
mybatis-plus:
  type-aliases-package: com.itheima.pojo
  mapper-locations: classpath:mapper/**/*Mapper.xml
  configuration:
    map-underscore-to-camel-case: true
    log-impl: org.apache.ibatis.logging.stdout.StdOutImpl

  global-config:
    db-config:
      id-type: auto             # 全局id类型为自增长
      update-strategy: not_null # 更新策略：只更新非空字段
```

## mybatis-plus中的条件构建器

构建一些复杂的增删改查任务
![[Pasted image 20251220162614.png]]

### 1.QueryWrapper
无论是查询，修改，删除，都可以使用QueryWrapper来构建条件：
