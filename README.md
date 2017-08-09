# SRKit
My Kit

###{转} 自己搭建服务器,获取数据测试 ###

1.安装Homebrew
2.安装Nginx
3.启动Nginx
4.配置JSON文件
5.配置Niginx


##1.在终端输入安装brew: ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
##2.在终端输入安装Nginx: brew install nginx
##3.在终端输入启动安装好的Nginx:nginx 
##4.前往文件夹:/usr/local/Cellar/nginx/  ->版本号 ->html ->创建一个aaa.json,在里面键入你要的数据
##5.前往文件夹:/usr/local/etc/ ->nginx  找到nginx.conf.default用文本编辑打开 copy数据:
server {        
    listen       8080;    
    server_name  localhost;         
    #access_log  logs/host.access.log  main; 
    location ~* {             
        add_header Content-Type "application/json";
        root   html;             
        if (!-f $request_filename) {                 
            rewrite ^/(.*)  /$1.json last;
        }             
    index  index.php index.html index.htm;
    }         
error_page 405 =200 http://$host$request_uri;     }

##6.在浏览器输入:localhost:8080/aaa.json 即可访问你的数据
##7.用Get 请求http://localhost:8080/aaa.json
##8.大功告成
