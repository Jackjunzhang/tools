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
  
  
  