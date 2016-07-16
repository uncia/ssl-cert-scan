# ssl-cert-scan
Get website's source ip by ssl certificate
执行 gcc sslscan.c -lpthread -lssl -lcrypto -std=c99 即可编译（前提是安装了 libopenssl ） （ PS：不兼容 MSVC）
使用 ./sslscan 网站域名 开始IP 结束 IP 即可开始扫描
因为考虑到 OpenSSL 太老，各种申请再释放，多线程必须使用锁，线程太多可能就假死了，所以限制在了 50 个线程。
建议加个 wrapper ，多进程扫描，一个进程一个段
