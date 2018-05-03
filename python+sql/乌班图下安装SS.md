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