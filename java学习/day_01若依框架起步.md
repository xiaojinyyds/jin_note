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
