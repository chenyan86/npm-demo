# test

## Project setup
```
yarn install
```

### Compiles and hot-reloads for development
```
yarn serve
```

### Compiles and minifies for production
```
yarn build
```

### Lints and fixes files
```
yarn lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

操作步骤
一、组件封装
1：在package文件夹中，封装一个或多个组件【ui-button】
2: 使用Vue插件模式, 这一步是封装组件中的重点，用到了Vue提供的一个公开方法：install。这个方法会在你使用Vue.use(plugin)时被调用，这样使得我们的插件注册到了全局，在子组件的任何地方都可以使用。
   在package目录下新建index.js文件，代码如文件所示，这一项工作就是将我们封装好的组件注册为全局组件，用到了Vue.component()方法，当使用Vue.use()时，我们的install方法便会执行。

二、组件打包
1: 修改我们项目得package.json文件，配置打包命令：
"package": "vue-cli-service build --target lib ./src/package/index.js --name pig-ui --dest pig-ui"
    打包命令解释：
    --target lib 关键字 指定打包的目录
    --name 打包后的文件名字
    --dest 打包后的文件夹的名称

2: 然后执行打包命令：npm run package
   打包执行完成后我们项目目录下就会多出一个pig-ui文件夹，存放的是打包后的文件。

三、发布到npm
1: 初始化package.json
    在pig-ui文件夹下初始化一个package.json文件。
    进入pig-ui目录，执行命令：npm init -y
    package.json文件中的name字段便是我们上传到npm仓库后的名称。注意：name名字尽量私有化，不能与线上的npm项目重名，否则会报错（403）

四、发布到npm仓库
1: 注册账号, 注意记住用户名、密码和邮箱，发布的时候可能会用到。
2: 设置npm源, 如果想要发布npm包，我们得吧我们得npm源切换为官方得源，命令如下：
    npm config set registry=https://registry.npmjs.org
3: 添加npm用户, 进入pig-ui目录，添加npm用户，执行命令：npm adduser
4: 在pig-ui目录下执行命令：npm publish

发布失败的原因查找
1: 可能是名字重复了，改了名字即可(pig-ui目录下package.json文件中的name字段)
2: 检查npm源是否为官方的源，还是淘宝镜像源
3: 查看npm的邮箱是否通过验证

五、从npm安装使用
1: 直接执行安装命令：npm install pig-ui-test 
2: 在main.js引用注册, 如demo所示
