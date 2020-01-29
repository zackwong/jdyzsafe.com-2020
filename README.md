jdyzsafe.com-2019
=============

金点原子保险柜中文官网2019年版


域名绑定、301转向及nginx配置
-----

新建配置文件: ``sudo nano /etc/nginx/sites-available/jdyzsafe.com``

编辑配置文件及保存: 

    server {
      listen 443 ssl http2;
      server_name www.jdyzsafe.com;
      ssl_certificate jdyzsafe.pem;
      ssl_certificate_key jdyzsafe.key;
      index index.html;
      root /srv/jdyzsafe.com-2019/_site;
      error_page 404 /Error.html;
      add_header Strict-Transport-Security "max-age=15768000" always;
      ssl_protocols TLSv1 TLSv1.1 TLSv1.2 TLSv1.3;
      ssl_ciphers HIGH:!aNULL:!MD5:!DH;
    }
    server {
        listen 443 ssl http2;
        server_name jdyzsafe.com;
        ssl_certificate jdyzsafe.pem;
        ssl_certificate_key jdyzsafe.key;
        return 301 https://www.jdyzsafe.com$request_uri;
    }
    server {
        listen 80;
        server_name jdyzsafe.com www.jdyzsafe.com;
        return 301 https://www.jdyzsafe.com$request_uri;
    }

建立链接: ``sudo ln -s /etc/nginx/sites-available/jdyzsafe.com /etc/nginx/sites-enabled/``

重启nginx: ``sudo service nginx restart``


下载及生成网站
-----

1. 下载网站源码: ``git clone git://github.com/zackwong/jdyzsafe.com-2019.git``

2. 进入源码根目录: ``cd jdyzsafe.com-2019``

3. 生成网站: ``jekyll build``


开发者
---------

* Zack Wong &lt;hzzzoo@126.com&gt;

