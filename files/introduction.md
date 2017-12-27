### 概述
Node.js是基于Chrome JavaScript运行时建立的一个平台，实际上它是对Google Chrome V8引擎进行了封装，它主要用于创建快速的、可扩展的网络应用。Node.js
采用事件驱动和非阻塞I/O模型，使其变得轻微和高效，非常适合构建运行在分布式设备的数据密集型实时应用。<br>
运行于浏览器的Javascript，浏览器就是Javascript代码的解析器，而Node.js则是服务器端JS的代码解析器，存于服务器端的JS代码由Node.js来解析和应用。<br>
JS解析器只是JS代码运行的一种环境，浏览器是JS运行的一种环境，浏览器为JS提供了操作DOM对象和window对象等接口。Node.js也是JS的一种运行环境，node.js为
交互式运行环境：PEPLJS提供操作文件、创建http服务、创建TCP、UDP服务等接口，所以Node.js可以完成其他后台语言能完成的工作。<br>
### 交互式运行环境：PEPL
Node.js提供了一个交互式运行环境，通过这个环境，可以立即执行JS代码，使用方法类似于Chrome浏览器中Firebug插件中的Console。<br>
在Linux环境进入终端后，属于"node"或者“nodejs”进入Node.js的交互式运行环境，Ctrl+d可以退出此环境。<br>
查看系统中安装的Node.js版本：`node -v or nodejs -v` <br>
运行JS文件，eg:`node file.js or nodejs file.js` <br>
### Node.js模块和包
- **模块**：Node.js官方提供了很多模块，这些模块分别实现了一种功能，如操作文件模块fs,构建http服务模块的http等，每个模块都是一个JS文件，当然也可以自己编写模
块。
- **包**：包可以将多个具有依赖关系的模块组织在一起，封装多个模块，以方便管理。Node.js采用了CommonJS规范，根据CommonJS规范规定，一个JS文件就是 一个模块，
而包是一个文件夹，包内必须包含一个JSON文件，命名package.json。一般情况下，包内bin文件夹存放二进制文件，包内的lib文件夹存放JS文件，包内的doc文件夹存
放文档，包内的test文件夹存放单元测试。package.json文件中需要包含的字段及包的使用。
- **npm包管理工具**：npm是node.js的包管理工具，npm定义了包依赖关系标准，我们使用npm主要用来下载第三方包和管理本地下载的第三方包。
