# homebrew如何安装mysql？
##  使用homebrew搜索mysql包  
brew search mysql

提示信息如下：
==> Formulae<br/>
automysqlbackup            mysql-client@5.7           mysql@5.6<br/>
mysql                      mysql-connector-c++        mysql@5.7 ✔(因为我已经安装了所以会显示对勾）<br/>
mysql++                    mysql-sandbox              mysqltuner<br/>
mysql-client               mysql-search-replace<br/>
==> Casks<br/>
homebrew/cask/mysql-connector-python     homebrew/cask/navicat-for-mysql<br/>
homebrew/cask/mysql-shell                homebrew/cask/sqlpro-for-mysql<br/>
homebrew/cask/mysql-utilities<br/>

##  使用install命令安装指定版本的mysql
brew install mysql@5.7<br/>

会提示如下信息，你需要将提示的三条命令放到终端执行一遍<br/>
If you need to have mysql@5.7 first in your PATH run:<br/>
  echo 'export PATH="/usr/local/opt/mysql@5.7/bin:$PATH"' >> ~/.zshrc<br/>

For compilers to find mysql@5.7 you may need to set:<br/>
  export LDFLAGS="-L/usr/local/opt/mysql@5.7/lib"<br/>
  export CPPFLAGS="-I/usr/local/opt/mysql@5.7/include"<br/>
  
在终端依次执行上面提示的三条命令<br/>
echo 'export PATH="/usr/local/opt/mysql@5.7/bin:$PATH"' >> ~/.zshrc<br/>
export LDFLAGS="-L/usr/local/opt/mysql@5.7/lib"<br/>
export CPPFLAGS="-I/usr/local/opt/mysql@5.7/include"<br/>

##  修改密码为'newpassword'
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'newpassword';<br/>

##  启动mysql数据库
mysql -uroot -pnewpassword<br/>
或者brew services start mysql@5.7<br/>

##  其他命令
brew services stop mysql@5.7  关闭mysql<br/>
brew services restart mysql@5.7  重启mysql<br/>
mysql.server start/stop/restart 启动/关闭/重启mysql<br/>
mysql.server start/stop/restart 启动/关闭/重启mysqlbrew<br/>
mysql.server start/stop/restart 启动/关闭/重启mysql<br/>
brew services list 查看brew服务列表状态<br/>
