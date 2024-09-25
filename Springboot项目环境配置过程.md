## Springboot 项目环境配置过程

### 工具
Intellij IDEA 集成化工具

### 前期准备工作
+ 数据库表
+ 下载好Maven、Tomcat等依赖

### 配置起步依赖

#### 创建Springboot项目
1. “新建项目”

2. 类型改为Maven，Next
3. 依赖项：勾选 `Developer Tools`：`Lombok`；`SQL`：`Mybatis Framwork`、`MySQL Driver`
4. 创建
   
#### 添加数据库
``` java
// .target/application.properties
spring.application.name=sprintboot-mybatis-quickstart

spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.datasource.url=jdbc:mysql://localhost:3306/cookieshop // "cookieshop"替换为数据库中的数据库名称，localhost表示主机，3306表示数据库运行的端口
spring.datasource.username=root
spring.datasource.password=B1619220912xc // password 后跟数据库的密码
```

#### 配置Maven
```
“文件”(File) -> "设置"(Settings) -> "构建、执行、部署" -> "构建" -> Maven -> Maven 主路径 D:\apache-maven-3.8.8-bin\apache-maven-3.8.8 -> "重写"用户设置文件 -> 用户设置文件 D:\apache-maven-3.8.8-bin\apache-maven-3.8.8\conf\settings.xml
```
#### 可视化DataBase
右侧引申栏下

"+" -> 数据源 -> MySQL -> 填写数据库相关信息 -> 用户名root -> 密码password -> 数据库:填写数据库名称——URL会变化 -> 应用(apply)

IDEA中可视化 DataBase 后，可以直接在IDEA打开控制台修改、添加、查看表

#### 引入Maven项目

右侧Maven工具栏 -> + -> 选择工程目录下的`pom.xml`

#### 配置Tomcat

文件 -> 项目结构 -> 
+ 左侧菜单栏 Modules 选项 -> 单击Sources配置项 -> 项目web文件夹下创建 `classes` 和 `lib` 文件夹 
  
+ 单击Paths配置项 -> 将`Output path`和`Test output path` 的地址改为 Sources 中配置的 `classes` 和 `lib` 文件夹
+ 单击 Dependencies 配置项 -> 关联所需 JAR 包
+ Dependencies 中，单击右侧【+】-> 【JARs or directories...】，在select path中选择创建 Web 项目的 lib 文件夹，单击【OK】按钮
+ RUN -> Edit Configurations... -> 左上角【+】按钮 -> Add New Configuration -> 选择Tomcat Server -> Local
+ name 后给配置的 Tomcat 命名，“Http port”后可给 Tomcat 规定端口号，默认是 `8080`，Configure 配置本地路径
+ 单击Deployment配置 -> 【+】->【Atrifact...】 项目部署
