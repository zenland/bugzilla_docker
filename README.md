这个项目是从github上面clone来的
项目原始github地址 https://github.com/bugzilla/docker-bugzilla-dev.git

# 运行
进入到docker-bugzilla-dev目录下面
运行 `docker-compose up`

# 注意事项
在启动容器时候遇到了一些问题，记录如下：
+ 启动容器以后，提示data/*文件不存在
  需要进入容器数据库中，运行以下命令
  
      CREATE USER 'bugs'@'localhost' IDENTIFIED BY 'bugs';
      GRANT ALL ON *.* TO 'bugs'@'localhost';
      CREATE DATABASE 'bugs';
  
  接着进入到` /var/www/html/` 目录下，运行 `perl checksetup.pl`
+ 可能因为权限无法访问页面（不一定会这样）：
  进入`/var/www/`目录下：
  运行：`chmod -R 775 ./*`
