## 第一步
电脑需要有node环境，推荐安装nodejs22版本以上，可以使用更多的AI终端工具。
下载链接：https://nodejs.org/en
```
https://nodejs.org/en
```
![[Pasted image 20251129142708.png]]
安装后我们可以通过终端命令 node -v来判断
![[Pasted image 20251129142809.png]]
## 第二步
我们来访问谷歌cli的官网，拿到下载命令
```
https://geminicli.com/
```
![[Pasted image 20251129142944.png]]
下载命令为：
```
npm install -g @google/gemini-cli
```
我们接下来在任意终端打开即可，运行上述命令。
## 第三步
获取gemini APIkey
我们选择的网站是谷歌的AIstudio(需要科学上网环境)

```
https://aistudio.google.com
```
![[Pasted image 20251129143236.png]]
找到左下角的get api key
点击进去，我们就可以新建项目和新建项目对应的apikey了
![[Pasted image 20251129143341.png]]
我们点击复制按钮，就可以把genimi api key给复制下来了
## 第四步
配置环境变量
![[Pasted image 20251129143502.png]]
我们找到系统环境变量，进行新建
![[Pasted image 20251129143547.png]]
变量名为GOOGLE_API_KEY，变量值为刚刚复制的google api key
![[Pasted image 20251129143655.png]]
## 第五步
验证gemini是否能正常使用
我们任意地方打开终端，输入启动命令gemini
![[Pasted image 20251129143833.png]]
出现这个就说明已经OK了，可以正常对话，每天有很多额度可以使用gemini2.5pro（免费用户）

## 异常情况
当对话后出现了长时间无响应，可能是代理的node没有被转发到gemini上（国外环境），这里需要我们改一下https和http的代理即可
```
$env:HTTP_PROXY="http://127.0.0.1:7890"
$env:HTTPS_PROXY="http://127.0.0.1:7890"
```