java 各种工具应用


rabbimq-server:

  启动命令：net stop RabbitMQ && net start RabbitMQ
  查看已有用户及用户的角色：rabbitmqctl.bat list_users
  新增一个用户：rabbitmqctl.bat add_user username password
  变成 “超级管理员” 角色：rabbitmqctl.bat set_user_tags username administrator
  更改密码：rabbitmqctl change_password userName newPassword
  干掉用户：rabbitmqctl.bat delete_user username
  
  使用浏览器打开 http://localhost:15672 访问Rabbit Mq的管理控制台
  
  
  
consul:  
  启动命令：consul agent -dev
  
  http://localhost:8500 
  
jenkins:
  默认用户名：admin
  默认密码在  C:\Users\HT\.jenkins\secrets\initialAdminPassword       （我的电脑用户名叫HT，看看您的是什么）
  cmd 进入jenkins.war 的所在文件夹，输入命令“java -jar jenkins.war”启动Jenkins
  
  
  
  
  
  
  
  
  
  
  
  
tomcat: 
      /home/apache-tomcat-8.5.34/bin/startup.sh 启动命令
      /home/apache-tomcat-8.5.34/bin/shutdown.sh 停止命令 
       tail -f catalina.out   进入tomcat/logs/文件夹下 ,查看日志
       ps –ef|grep tomcat    查看启动的tomcat端口 
       kill -9 7010           杀死tomcat进程7010

       Tomcat启动时卡在[localhost-startStop-1] org.apache.catalina.startup.HostConfig.deployDirectory
       解决方法：JVM上的随机数与熵池策略：命令行生成较低强度密码的伪随机数（cat /dev/urandom | od -x |        head -10），然后在catalina.sh中加入这么一行：-Djava.security.egd=file:/dev/./urandom


      This is very likely to create a memory leak问题解决？
      解决方法：tomcat/bin 目录下的catalina.sh添加：JAVA_OPTS=’-Xms512m -Xmx1024m’
                或者 JAVA_OPTS=”-server -Xms800m -Xmx800m -XX:MaxNewSize=256m”
                或者 CATALINA_OPTS=”-server -Xms256m -Xmx300m”   
				
				
				
  
mysql:

     name:root
     password:Zj_123456  

     1.mysql社区版安装
     2.centos7.4开放3306端口权限
     3.阿里云服务器设置安全端口权限
     4.远程连接需设置MySQL ip访问权限
     5.需关闭防火墙   

 一、启动方式
1、使用linux命令service 启动：
service mysqld start
2、使用 mysqld 脚本启动：
/etc/inint.d/mysqld start
3、使用 safe_mysqld 启动：
safe_mysqld&

二、停止
1、使用 service 启动：
service mysqld stop
2、使用 mysqld 脚本启动：
/etc/inint.d/mysqld stop
3、 mysqladmin shutdown

三、重启
1、使用 service 启动：
service mysqld restart
2、使用 mysqld 脚本启动：
/etc/inint.d/mysqld restart

备注：查看mysql端口是否已经使用，使用netstat -anp 命令查看服务器端口使用情况。	 
	 


nginx:
      安装：
          1.检查并安装Nginx基础依赖包pcre-devel   openssl-devel
            yum install -y openssl-devel pcre-devel
          2.开始安装Nginx 操作命令如下：
            1>创建nginx目录
              mkdir -p /home/tools  
            2>进入目录
              cd /home/tools/    
            3>下载软件包
               wget http://nginx.org/download/nginx-1.12.2.tar.gz
            4>查看文件详细信息
               ls -l nginx-1.12.2.tar.gz

               useradd -M -s /sbin/nologin nginx
            5>安装nginx
              tar zxf nginx-1.12.2.tar.gz 

              cd nginx-1.12.2/

              ./configure --prefix=/usr/local/nginx --with-http_dav_module --with-              http_stub_status_module  --with-http_addition_module --with-http_sub_module  --with-              http_flv_module --with-http_mp4_module --with-pcre --with-http_ssl_module --with-              http_gzip_static_module  --user=nginx  --group=nginx 

              make && make install
            6>安装后优化
              ln -s /usr/local/nginx/sbin/nginx /usr/local/sbin/
            7>启动
              nginx
              
              netstat -anput | grep nginx（可看信息为80端口）

              firewall-cmd --permanent --zone=public --add-port=80/tcp	 
			  
			  
			  
			  

防火墙:
     systemctl status firewalld  查看firewalld状态
     systemctl start firewalld   开启防火墙
     firewall-cmd --permanent --zone=public --add-port=3306/tcp 永久开启端口
     systemctl stop firewalld    关闭防火墙设置			  
	 


	 

docker:
  1.自身安装
  2.安装RabbitMQ
    a.docker pull rabbitmq:3.7.7-management(安装)
    b.docker run -d --hostname myrabbit --name rabbit -p 15672:15672 -p 5672:5672 rabbitmq:3.7.7-management（运行）

    
  
  
  