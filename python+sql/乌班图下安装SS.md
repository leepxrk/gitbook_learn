#### 乌班图安装ss

    自己有翻墙查一些资料的需要，同时在折腾乌班图系统，翻墙就成了一个大问题。在这里把乌班图16.04下安装ss的过程记录下来。

**安装python - pip**
1. sudo apt-get update
2. sudo apt-get install python-pip

**使用pip安装ss**
1. sudo pip install shadowsocks

**使用命令行运行**</br>
sslocal -s 1.1.1.1 -p 8766 -k"your password" -b 127.0.0.1 -l 1080 -m 加密方式

其中
1. sslocal 是启动命令
2. s 后填写服务器地址
3. p 服务端端口号
4. k 连接密码,字符类型为string，需要填写在双引号之间
5. b local 本地域名，一般默认为127.0.0.1
6. l 本地端口地址，一般默认为1080
7. m 加密方式，默认使用aes-256-cfb加密方式

**使用文件运行**


*字段释义如下*

|    字段名称    |       字段释义       |
|:--------------:|:-------------------- |
|   sslocal      | ss的启动命令         |
|         s      | 服务器IP地址         |
|         p      | 服务器远程访问的端口号     |
|         k      | 连接密码　　         |
|         b      | 本地域名，默认为127.0.0.1  |
|         l      | 本地端口地址，默认为1080   |
|         m      | 加密方式，默认为aes-256-cfb加密    |


**使用文件运行**
1. 在任何你喜欢的目录下，创建一个json文件（没有新建按钮就用vi 新建一个文件好了）
2. 格式如下,字段释义见上表(注意：端口号还有时间等信息是int类型的格式，不需要双引号)

```json
{
	"server":"服务器IP",
    "server_port":远程端口号,
    "local_address":"127.0.0.1",
    "local_port":1080,
    "password":"访问密码",
    "timeout":600,
    "method":"aes-256-cfb",
    "auth": true
}
```


３. 在当前目录下，使用命令行运行
```
启动ss：sslocal -c shadowsocks.json start
停止ss：sslocal -c shadowsocks.json stop
```


*我本人比较懒，就在当前目录下新建了两个sh文件分别对应启动ss和停止ss，直接用sh 脚本文件名.sh来运行，例如sh ss_start.sh，执行后即可启动ss*

启动ss：sh ss_start.sh
```sh
#！/bin/bash
#shadow.sh
sslocal -c shadowsocks.json start
```

停止ss：sh ss_stop.sh
```sh
#！/bin/bash
#shadow.sh
sslocal -c shadowsocks.json stop
```
</br>

**多账号管理** </br>
在json文件内增加多账号管理逻辑，简单来说就是设置每个“访问端口”有独立的“访问密码”。</br>
示例如下：

```json
{
	"server":"服务器IP",
    "local_address":"127.0.0.1",
    "local_port":1080,
    "port_password":
    {
    "访问端口号1":"端口对应密码",
    "访问端口号2":"端口对应密码",
    ……
    "访问端口号n":"端口对应密码"
    },
    "timeout":600,
    "method":"aes-256-cfb",
    "auth": true
}
```

</br>
**多账号管理之bsp** </br>
因为么有限制流量的需求，所以没有安装bsp，如果有这方面需求的同学，可以到bsp的gitHub看一下。安装和操作都比较简单，需要注意的是需要修改bsp的配置文件，指向shadoasock.json文件才能实现修改的功能。具体的可以在bsp的github中看见，我就不赘述了。

