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
### 借助pm2让node.js常驻
1.让服务稳定持续的运行 <br>
> 服务端运行app.js 通过浏览器访问，发现OK，但是ctrl+C或者Ctrl+Q发现只要从终端退出，那肯定是挂了，显然这不是我们要的结果。我们的需求是，让它能长久的在后台运行，即便发生意外挂掉也能自动重启，解决这个问题的方案就是**pm2**
pm2作用：
- 运维node本身
- 发生意外自动重启
- 收集日志
```
因为之前已经安装过，所以可以直接用pm2
pm2 start app.js
pm2 list //可以查看开启的所有node服务
pm2 show app //查看详细信息
pm2 logs 
ctrl+C //exit

```




