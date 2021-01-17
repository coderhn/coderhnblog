# 一、下载依赖



## 1.初始化项目和git仓库并安装相关依赖

```javascript
git init
npm init -y
npm install express mysql2 sequelize sequelize-cli body-parse -S
```

## 2.配置nodemon自动监听文件变化重启服务

```javascript
npm install nodemon -D//注意是参数只能是-D
//1. 注意为了防止nodemon不必要的重启，需要配置nodemon.json
//2. 在项目根目录下创建nodemon.json文件
{
  "watch":["./src/**/*.js"]//只监听src目录下的.js文件
}
//3. nodemon集成了测试日志，如果需要查看debug日志，可以如下配置package.json
{
  wo
}
```



## 二、更改配置文件package.json

node应用程序默认更改完了代码不会自动重启，需要安装nodemon依赖并配置它

```javascript
 "scripts": {
    "start": "nodemon ./src/app.js",//在入口文件前加nodemon
  },
```

# 三、ORM模型创建

## 1.创建数据库

### (1).首先检查系统中mysql服务是否开启

```
brew services list
//或者
brew services list | grep mysql

mysql -u root -p123456
create database demo
```

### (2).使用sequelize cli初始化项目的数据库配置信息

```java
//为了防止sequelize cli初始化数据库配置信息时影响其他文件夹，我们单独为数据库配置创建一个文件夹
npm install sequelize-cli -D
mkdir db
cd db
npx sequelize init
```

### (3).生成模型文件

```javascript
//1. migrate 文件
//2. model 文件
npx sequelize model:generate --name Todo --attributes name:string,deadline:date,content:string
```

### (4).持久化，模型对应的[数据库表]

```javascript
npx sequelize db:migrate
```

# 四、nrm管理npm源

```javascript
nrm ls//查看所有npm源
nrm current//查看当前npm源
nrm use 源名//即可配置npm源
```

# 五、nvm管理nodejs版本

