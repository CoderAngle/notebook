## 介绍

```
利用jenkins 自动化部署github，这样只需要在本地提交项目到github就可以了，剩下的全交给Jenkins自动部署
```

## 配置github

### webhooks

> payload url 后面会配置到，等会过来配置

![](../../assets/20200913132735.png)

![](../../assets/jtbg-2.png)

### 

### access tokens

点击在右上角**settings**，剩下如下操作

![](../../assets/jtbg-5.png)

![](../../assets/jtbg-3.png)

> 注意，记下当前密钥

## jenkins配置

如下操作

![](../../assets/jtbg-6.png)

### 配置ssh

* 先填下对应信息

![](../../assets/jtbg-7.png)

* 然后配置凭据

![](../../assets/jtbg-8.png)

* 用户名:服务器账号
* 密码:服务器密码
* ID:自定义
* 描述:自定义

然后在Credentials选择刚才创建的凭据，然后点击Check connection会出现如下类似信息

```
Successfull connection
```

### GitHub配置

点击高级选项，然后先配置如下信息

![](../../assets/jtbg-10.png)

* 在Hook URL处的ur记住，这个地址应该填在上面所述的payload url 处
* 名称:自定义
* API URL:不能修改
* 凭据:如下

![](../../assets/jtbg-11.png)

* secret：填写刚才在github生成的密钥
* ID:自定义
* 描述:自定义

### Git配置

![](../../assets/jtbg-12.png)

### 

### Publish over SSH

步骤简单，就不说了

![](../../assets/jtbg-13.png)

### 创建Job

点击首页的新建任务，自定义任务名称，然后选择构建一个自由风格的软件项目

填写如下

#### github 配置

![](../../assets/jtbg-14.png)

#### git 配置

![](../../assets/jtbg-17.png)

#### 配置git凭据

![](../../assets/jtbg-16.png)

* 用户名:github用户名或者邮箱
* 密码:github账号密码
* ID和描述:自定义

### 构建触发器

如图勾选，这样，当本地提交项目到github时，就能够自动触发进行部署

![](../../assets/jtbg-18.png)

到这样里，就可以已经完成了，自动化部署，等下进行测试

### 构建

由于自动化部署的项目，没有部署到理想的路，因此在这里执行远程命令，将项目移动正确的位置

![](../../assets/jbtg-19.png)

* SSH SITE:在前面已经配置好了，选中即可
* Command:这里是远程在服务器命令行中所执行的命令

```
利用cp命令进行覆盖和rm -rf 删除
```



