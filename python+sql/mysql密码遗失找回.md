### mysql密码遗失找回方案


#### 开放远程链接

使用如下命令创建远程连接账号
GRANT ALL PRIVILEGES ON *.* TO 'user_name'@'%' IDENTIFIED BY 'password' WITH GRANT OPTION;


例
GRANT ALL PRIVILEGES ON *.* TO 'rocklee'@'%' IDENTIFIED BY 'zxcvb19900807??' WITH GRANT OPTION;


##### 执行如下命令使得设置生效
flush privileges;