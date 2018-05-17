#### 乌班图安装ss

自己有翻墙查一些资料的需要，同时在折腾乌班图系统，翻墙就成了一个大问题。在这里把乌班图16.04下安装ss的过程记录下来。
</br>

**安装python - pip**
```
sudo apt-get update
sudo apt-get install python-pip
```

</br>
**使用pip安装ss**
```
sudo pip install shadowsocks
```
</br>
**使用命令行运行**
```
sslocal -s 1.1.1.1 -p 8766 -k"your password" -b 127.0.0.1 -l 1080 -m 加密方式
```

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

</br>
**使用文件运行**
1. 在任何你喜欢的目录下，创建一个json文件（没有新建按钮就用vi 新建一个文件好了）
2. 格式如下,字段释义见上表

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


