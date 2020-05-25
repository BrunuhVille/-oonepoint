https://www.onesrc.cn/p/how-to-deploy-onepoint-on-linux.html
如何在 linux 上部署 onepoint
按照这篇文章安装的。centos7
~~~
安装nodejs
mkdir -p /usr/local/lib/nodejs
wget https://nodejs.org/dist/v13.14.0/node-v13.14.0-linux-x64.tar.xz
tar -xJvf node-v13.14.0-linux-x64.tar.xz -C /usr/local/lib/nodejs
ln -sf /usr/local/lib/nodejs/node-v13.14.0-linux-x64/bin/node /usr/local/bin/
ln -sf /usr/local/lib/nodejs/node-v13.14.0-linux-x64/bin/npm /usr/local/bin/
ln -sf /usr/local/lib/nodejs/node-v13.14.0-linux-x64/bin/npx /usr/local/bin/
安装成功，输入命令有效
安装pm2
npm install -g pm2
ln -s /usr/local/lib/nodejs/node-v13.14.0-linux-x64/bin/pm2 /usr/local/bin/pm2
安装成功，输入命令有效
下载源码
yum install unzip -y
wget https://github.com/ukuq/onepoint/archive/master.zip
unzip master.zip
cd onepoint-master/
npm install
运行
iptables -I INPUT -m state --state NEW -m tcp -p tcp --dport 8020 -j ACCEPT
iptables -I INPUT -m state --state NEW -m udp -p udp --dport 8020 -j ACCEPT
pm2 start bin/index_node.js
输入后pm2有显示一个表格的东西
~
