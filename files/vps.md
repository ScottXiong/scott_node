### 环境搭建
```
sudo apt-get install vim openssl build-essential libssl-dev wget curl git 
再github上找到nvm，下载自动安装执行脚本--nvm
wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | bash
提示重新打开窗口，重新登录
nvm ／／测试有没安装成功
nvm install v6.9.5  ／／安装v6.9.5，具体以官网版本为准
nvm use v6.9.5   //指定版本
nvm alias default v6.9.5   //系统指定默认版本
node -v
npm --registry=https://registry.npm.taobao.org install -g npm 
npm -v
echo fs.inotify.max_user_watchers=524288 | sudo tee -a /etc/sysctl.conf && sudo sysctl -p
输入密码，ok
npm install -g cnpm --registry=https://registry.npm.taobao.org
cnpm -v
//cnpm sync koa 当npm安装不上的时候，可以通过cnpm sync将国外的模块强制拉到国内的镜像上去
npm i pm2 webpack gulp grunt-cli -g ／／全局安装包
```
### 测试
```
ls
vim app.js
//确认输入法为英文输入法
const http=require('http')
http.createServer(function(req,res){
	res.writeHead(200,{'Content-Type':'text/plain'})
	res.end('Hello,my name is Scott')
}).listen(8898)
console.log('server is running ....')
如果改了端口，配置了防火墙，可能会报错，这时我们要更改防火墙设置，新开一个窗口：
sudo vi /etc/iptables.up.rules
在allow http https 下新增一行
-A INPUT -p tcp --dport 8898 -j ACCEPT //（新增一道门）想开放哪个端口就开放哪个端口
保存，退出
sudo iptables-restore < /etc/iptables.up.rules  //重载一下，再通过ip的方式访问，it's OK。 
```

