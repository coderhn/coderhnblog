# homebrew如何安装mysql？
##  使用homebrew搜索mysql包  
### brew search mysql

==> Formulae
automysqlbackup            mysql-client@5.7           mysql@5.6
mysql                      mysql-connector-c++        mysql@5.7 ✔(因为我已经安装了所以会显示对勾）
mysql++                    mysql-sandbox              mysqltuner
mysql-client               mysql-search-replace
==> Casks
homebrew/cask/mysql-connector-python     homebrew/cask/navicat-for-mysql
homebrew/cask/mysql-shell                homebrew/cask/sqlpro-for-mysql
homebrew/cask/mysql-utilities

##  使用install命令安装指定版本的mysql
### brew install mysql@5.7

会提示如下信息，你需要将提示的三条命令放到终端执行一遍
If you need to have mysql@5.7 first in your PATH run:
  echo 'export PATH="/usr/local/opt/mysql@5.7/bin:$PATH"' >> ~/.zshrc

For compilers to find mysql@5.7 you may need to set:
  export LDFLAGS="-L/usr/local/opt/mysql@5.7/lib"
  export CPPFLAGS="-I/usr/local/opt/mysql@5.7/include"
  
### echo 'export PATH="/usr/local/opt/mysql@5.7/bin:$PATH"' >> ~/.zshrc
### export LDFLAGS="-L/usr/local/opt/mysql@5.7/lib"
### export CPPFLAGS="-I/usr/local/opt/mysql@5.7/include"

##  修改密码为'newpassword'
### ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'newpassword';

##  启动mysql数据库
### mysql -uroot -pnewpassword
### 或者brew services start mysql@5.7

##  其他命令
### brew services stop mysql@5.7  关闭mysql 
### brew services restart mysql@5.7  重启mysql
### mysql.server start/stop/restart 启动/关闭/重启mysql
### mysql.server start/stop/restart 启动/关闭/重启mysqlbrew
### mysql.server start/stop/restart 启动/关闭/重启mysql
### brew services list 查看brew服务列表状态
