
基于django的视频点播网站开发
依赖Python3.7.nginx，MySQL

nginx配置文件示例


 upstream django {
    server 127.0.0.1:9001;
   }

    server {
    listen 80;
    server_name 172.16.6.42; 
    location /static/ {
           alias /u02/videoproject/static/;
        }

    location /upload/ {
           alias /u02/videoproject/upload/;
        }


     location / {
             include         uwsgi_params;
            uwsgi_pass      django;
        }
}
