# JenkinsDeploy
关于Jenkins的部署及配置前端项目的构建
本文记录在tomcat中部署Jenkins
## 安装JDK
## 安装Tomcat
## 下载Jenkins
##### 1.wget http://mirrors.jenkins-ci.org/war/latest/jenkins.war
##### 2.将Jenkins.war放入 $PATH/tomcat-xxx/webapps 中
##### 3.重启tomcat自动解压Jenkins.war
##### 4.此时访问http://192.168.xx.xx:8080/jenkins 即可打开，首次登录密码存放在$PATH/tomcat8/webapps/jenkins/secrets/initialAdminPassword
##### 5.插件的安装选择推荐即可，后期需要什么插件再安装
## 配置前端构建部署view
#### 安装Publish over SSH（用于构建完成后见打包文件部署至服务器）
##### 1.在Manage Jenkins 中的Manage Plugins中找到Publish over SSH并安装
##### 2.在Manage Jenkins 中的Configure System中配置Publish over SSH
##### 3.Passphrase即填写服务器的密码或者使用ssh key 的方式生成密钥
##### 4.配置SSH Server
![image](https://user-images.githubusercontent.com/20660091/140594281-82922c07-7bda-47e9-9082-c6030b45161a.png)
<br />有多个即配置多个SSH Server即可
#### 新建、配置Item
##### 1.点击‘新建Item’，给自己的任务填写一个名字，选择Freestyle Project
##### 2.首先勾选 This project is parameterized ,用于配置构建项目前可选性（比如需要打包哪个分支、需要发布到哪个环境）
![image](https://user-images.githubusercontent.com/20660091/140594432-3fad8ca0-f25b-4c2e-9a6f-5197b6c5c859.png)
![image](https://user-images.githubusercontent.com/20660091/140594455-e71682e3-789f-4cf1-a6c7-263075568ec1.png)
<br />此步骤需要安装Extended Choice Parameter Plugin
##### 3.配置git
![image](https://user-images.githubusercontent.com/20660091/140594637-cbc6d345-bfb2-4aab-976c-8d24e051116e.png)
##### 4.配置构建环境，添加构建命令
  ![image](https://user-images.githubusercontent.com/20660091/140595135-2d814af2-9441-47e3-8649-fdd809bd840e.png)
  <br />我这边选择我需要的node环境，配置了前端构建的shell命令
##### 5.配置构建后操作
<br />如果有多个需要部署的服务器即添加多个SSH Server
![image](https://user-images.githubusercontent.com/20660091/140595148-22720329-58b6-4cba-b81e-c485a41b7738.png)
## 最后
![image](https://user-images.githubusercontent.com/20660091/140605007-00e69d51-daff-42af-a8f4-452bc052edc7.png)
