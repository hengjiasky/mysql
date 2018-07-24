MySQL8.0的安装及配置
--
#1：配置：my.ini，配置文件见附件

#2：配置环境变量，将bint添加到path

#2：接下来开始安装，在CMD下运行
mysqld --initialize --user=mysql --console
#生成初始密码，并记录下来，执行下一步

mysqld --install
#服务注册安装

mysql -u root -p
#登录

ALTER USER "root"@"localhost" IDENTIFIED  BY "123456";
#修改密码
