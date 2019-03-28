---
layout: post
title:  "리눅스 바이너리 설치"
date:   2019-03-25 16:01:00
author: uni
categories: Rinux CentOS7 MariaDB
cover:  "/assets/header_image4.png"
---

소스컴파일 설치

Yum update


Yum install wget


yum install cmake make gcc gcc-c++ ncurses-devel libevent openssl openssl-devel
 
 
 <img  src="/assets/images/so1.jpg">

Wget<a hrep="https://downloads.mariadb.org/interstitial/mariadb-10.3.13/source/mariadb-10.3.13.tar.gz"> https://downloads.mariadb.org/interstitial/mariadb-10.3.13/source/mariadb-10.3.13.tar.gz
 </a>
 
 
<img  src="/assets/images/so2.jpg">


Tar zxvf mariadb-10.3.13.tar.gz


 <img  src="/assets/images/so3.jpg">

mkdir /data
mkdir /maradb/build
cd /mariadb/build


cmake .. 
 
<img  src="/assets/images/so4.jpg">


make&&make install
 
 
<img  src="/assets/images/so5.jpg">


ln -s mysql mariadb<br>
groupadd mysql<br>
useradd -g mysql mysql<br>
chown -R mysql.mysql /usr/local/mariadb<br>
chown -R mysql.mysql /data<br>
chown -R mysql.mysql /usr/local/mysql<br>



cd /usr/local/mariadb/scripts<br>

./mysql_install_db --datadir=/data --basedir=/usr/local/mariadb<br>
 
 <img  src="/assets/images/so6.jpg">
vi /etc/my.cnf<br>

basedir=/usr/local/mariadb<br>
datadir=/data<br>
[client]<br>
socket=/var/lib/mysql/mysql.sock<br>


 
<img  src="/assets/images/so7.jpg">

vi /usr/local/mariadb/support-files/mysql.server<br>
45, 46번째줄
 
<img  src="/assets/images/so8.jpg">

service mysqld start<br>
 <img  src="/assets/images/so9.jpg">


Cd /usr/local/mariadb/bin<br>
./mysql -uroot -p


 <img  src="/assets/images/so10.jpg">





 






