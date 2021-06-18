# bug-
在软件使用以及课程学习中会遇到很多bug，将要记录这些bug的问题
Anaconda更新一直报错，修改为国内镜像也不好使，最终找到了未被屏蔽的镜像。

错误日志：

UnavailableInvalidChannel: The channel is not accessible or is invalid.
  channel name: simple
  channel url: http://pypi.douban.com/simple
  error code: 404
意思是资源路径无效或无法访问；资源的url地址是 http://pypi.douban.com/simple，错误代码是404。

404是指链接指向的网页不存在，即原始网页的URL失效。

解决办法：

1.首先恢复配置： conda config --remove-key channels

 conda config --remove-key channels 

2.再配置镜像： Anaconda 2019-12-17目前可使用镜像：https://repo.continuum.io/pkgs/free/win-64/  https://repo.continuum.io/pkgs/main/win-64/

conda config --add channels https://repo.continuum.io/pkgs/free/win-64/
conda config --add channels https://repo.continuum.io/pkgs/main/win-64/ 
conda config --set show_channel_urls yes
3.查看配置信息：

conda config --show channels
pip源修改为国内镜像

国内镜像：

  阿里云  　　http://mirrors.aliyun.com/pypi/simple/ 
  中国科技大学  　　https://pypi.mirrors.ustc.edu.cn/simple/ 
  豆瓣(douban) 　　http://pypi.douban.com/simple/ 
  清华大学 　　https://pypi.tuna.tsinghua.edu.cn/simple/ 
  中国科学技术大学 　　http://pypi.mirrors.ustc.edu.cn/simple/

修改源方法：

临时使用： 
　　可以在使用pip的时候在后面加上-i参数，指定pip源 
　　eg: pip install scrapy -i https://pypi.tuna.tsinghua.edu.cn/simple

永久修改： 
linux: 
　　修改 ~/.pip/pip.conf (没有就创建一个)， 内容如下：

[global]
 index-url = https://pypi.tuna.tsinghua.edu.cn/simple
windows: 

　　直接在user目录中创建一个pip目录，如：C:\Users\xx\pip，在pip 目录下新建文件pip.ini，内容如下

　　或者按照网友的建议：win+R 打开用户目录%HOMEPATH%，在此目录下创建 pip 文件夹，在 pip 目录下创建 pip.ini 文件, 内容如下

[global]
timeout = 6000
index-url = https://pypi.tuna.tsinghua.edu.cn/simple
trusted-host = pypi.tuna.tsinghua.edu.cn
