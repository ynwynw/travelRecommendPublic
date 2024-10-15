## 本项目完整源码是收费的  接毕业设计和论文

### 作者微信：grapro666 QQ：3642795578 (支持部署调试、支持代做毕设)

### 接javaweb、python、小程序、H5、APP、各种管理系统、单片机、嵌入式等开发

### 选题+开题报告+任务书+程序定制+安装调试+论文+答辩ppt

**博客地址：
[https://blog.csdn.net/2303_76227485/article/details/142924338](https://blog.csdn.net/2303_76227485/article/details/142924338)**

**视频演示：
[https://www.bilibili.com/video/BV1gTmGYCEif/](https://www.bilibili.com/video/BV1gTmGYCEif/)**

**毕业设计所有选题地址：
[https://github.com/ynwynw/allProject](https://github.com/ynwynw/allProject)**

## 基于Java+Springboot+vue的景区旅游推荐管理系统(源代码+数据库+7000字论文)190

## 一、系统介绍
本项目前后端分离，分为用户、管理员两种角色，带协同过滤算法，皮尔森（pearson）相关系数计算
### 1、用户：
- 注册、登录、景点推荐(预约、评论)、旅游线路、酒店预订、旅游资讯、我的收藏、我的预订、个人信息、密码修改
### 2、管理员：
- 景点预约统计、酒店预约统计、景点管理、线路管理、酒店管理、资讯管理、景点预约管理、酒店预约管理、轮播图管理、个人中心、用户管理、管理员管理

## 二、所用技术

后端技术栈：

- Springboot
- mybatisPlus
- Redis
- Mysql
- Maven

前端技术栈：

- Vue
- Vue-router
- axios
- elementUi
- echarts

## 三、环境介绍

基础环境 :IDEA/eclipse, JDK1.8, Mysql5.7或以上, Maven3.6, node14, navicat

所有项目以及源代码本人均调试运行无问题 可支持远程调试运行

## 四、页面截图
### 文档目录：
![contents](./picture/picture0.png)
![contents](./picture/picture00.png)
![contents](./picture/picture000.png)
### 1、用户：
![contents](./picture/picture1.png)
![contents](./picture/picture2.png)
![contents](./picture/picture3.png)
![contents](./picture/picture4.png)
![contents](./picture/picture5.png)
![contents](./picture/picture6.png)
![contents](./picture/picture7.png)
![contents](./picture/picture8.png)
![contents](./picture/picture9.png)
![contents](./picture/picture10.png)
![contents](./picture/picture11.png)
![contents](./picture/picture12.png)
![contents](./picture/picture13.png)
![contents](./picture/picture14.png)
![contents](./picture/picture15.png)
![contents](./picture/picture16.png)
![contents](./picture/picture17.png)

### 2、管理员：
![contents](./picture/picture18.png)
![contents](./picture/picture19.png)
![contents](./picture/picture20.png)
![contents](./picture/picture21.png)
![contents](./picture/picture22.png)
![contents](./picture/picture23.png)
![contents](./picture/picture24.png)
![contents](./picture/picture25.png)
![contents](./picture/picture26.png)
![contents](./picture/picture27.png)
![contents](./picture/picture28.png)
![contents](./picture/picture29.png)
![contents](./picture/picture30.png)
![contents](./picture/picture31.png)
![contents](./picture/picture32.png)
![contents](./picture/picture33.png)
![contents](./picture/picture34.png)
![contents](./picture/picture35.png)

## 五、浏览地址
前台地址：http://localhost:3001

用户账号密码：user/123456

后台地址：http://localhost:3000

管理员账户密码：admin/123456

## 六、部署教程
1. 使用Navicat或者其它工具，在mysql中创建对应名称的数据库，并执行项目的sql文件

2. 使用IDEA/Eclipse导入backend-Api项目，若为maven项目请选择maven，等待依赖下载完成

3. 修改application.yml里面的数据库配置,src/main/java/com/SpringbootSchemaApplication.java启动后端项目

4. vscode或idea打开user-frontend项目

5. 在编译器中打开terminal，执行npm install 依赖下载完成后执行 npm run dev,执行成功后会显示前台访问地址

6. vscode或idea打开admin-frontend项目

7. 在编译器中打开terminal，执行npm install 依赖下载完成后执行 npm run dev,执行成功后会显示后台访问地址

## 七、亮点
1、使用协同过滤算法，皮尔森（pearson）相关系数计算，进行景点推荐
