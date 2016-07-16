# ssl-cert-scan
Get website's source ip by ssl certificate

有的时候，网站为了隐藏自己的源站 IP 使用了 CDN ，怎么把它揪出来呢？有一种快速方便的办法就是扫 SSL 证书上的域名。
（只针对能通过 HTTPS 访问的网站，HTTP 以后再说）

执行 gcc sslscan.c -lpthread -lssl -lcrypto -std=c99 即可编译（前提是安装了 libopenssl ） （ PS：不兼容 MSVC）
使用 ./sslscan 网站域名 开始IP 结束 IP 即可开始扫描
因为考虑到 OpenSSL 太老，各种申请再释放，多线程必须使用锁，线程太多可能就假死了，所以限制在了 50 个线程。
建议加个 wrapper ，多进程扫描，一个进程一个段
