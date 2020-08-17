## docker 安装

```

```

## hexo 后台运行

### 安装forever

```
npm install -g forever
```

### 新建app.js

安装完成，还不能直接用，需要在你的hexo根目录下新建一个js文件，比如app.js,代码如下：

```
require('hexo').init({command: 'server'});
```

### 运行

之后使用命令`forever start app.js`即可。

查看forever进程命令`forever list`, 更多命令输入`forever -h`

