---
layout: post
title:  "리눅스 바이너리 설치"
date:   2019-03-25 16:01:00
author: uni
categories: Rinux CentOS7 MariaDB
cover:  "/assets/header_image4.png"
---


<h2>yum으로 wget 설치</h2>




<h4> yum install wget</h4>

 
<img  src="/assets/images/bi1.jpg">




<h2>wget으로 MariaDB 다운로드</h2>

<h4>wget https://downloads.mariadb.org/f/mariadb-10.3.13/bintar-linux-x86_64/mariadb-10.3.13-linux-x86_64.tar.gz</h4>
 
<a href="https://downloads.mariadb.org/f/mariadb-10.3.13/bintar-linux-x86_64/mariadb-10.3.13-linux-x86_64.tar.gz">https://downloads.mariadb.org/f/mariadb-10.3.13/bintar-linux-x86_64/mariadb-10.3.13-linux-x86_64.tar.gz</a>
 
<img  src="/assets/images/bi2.jpg">



<h2>압축풀기</h2>

<br>
<h4>tar zxvf mariadb-10.3.13-linux-x86_64.tar.gz </h4>

 <br>

 
<img  src="/assets/images/bi3.jpg">




<h2>mv로 local로 이동후 설정값 세팅</h2>

<h4>mv mariadb-10.3.13-linux-x86_64/ /usr/local/</h4>
<br>
<h2>퍼블릭링크설정</h2>
<h4>cd /usr/local/

<br>
ln -s usr/local/mariadb-10.3.13<tab> mariadb
<br>
<h4>
groupadd mysql

<br>
useradd -g mysql mysql

<br>
cd 
mkdir /data
<br>

mkdir /log

<br>
chown -R mysql.mysql(groupid.userid) /usr/local/mariadb (파일위치)

<br>
chown -R mysql.mysql /usr/local/mariadb
<br>

chown -R mysql.mysql /data

<br>
chown -R mysql.mysql /log


 </h4>
 
<img  src="/assets/images/bi4.jpg">




<br>
<h2>my.cnf설정</h2>


<br>
<h4>vi /etc/my.cnf

<br>
datadir=/DATA


<br>
basedir=/usr/local/mariadb

 </h4>

 
<img  src="/assets/images/bi5.jpg">





<h2>install</h2>

<h4>
/usr/local/mariadb/scrips/mysql_install_db --basedir=/usr/local/mariadb --defaults-file=/etc/my.cnf</h4>
 

 
<img  src="/assets/images/bi6.jpg">



<h2>설정값 설정</h2>



<h4>cd /usr/local/mariadb/support-flies


<br>
cp mysql.server /etc/init.d/mysqld

<br>

vi /etc/init.d/mysqld
<br>


45, 46번째 줄 데이터변경


<br>
datadir= /data


<br>
basedir=/usr/local/mariadb

 </h4>

 
<img  src="/assets/images/bi7.jpg">





<h2>설정값설정</h2>



<h4>chown -R mysql.mysql /data</h4>
 

 
<img  src="/assets/images/bi8.jpg">



<h2>MariaDB 시작준비</h2>



<h4>service mysqld start</h4>
 

 
<img  src="/assets/images/bi9.jpg">



<h2> 설정값 설정 </h2>



<h4>vi /usr/local/mariadb/support-files/mysql.server</h4>



45, 46번째줄 수정

<br>

datadir= /data

<br>

basedir=/usr/local/mariadb
 
<br>
 
<img  src="/assets/images/bi10.jpg">




<h2>설정값 추가</h2>


<br>

/etc/my.cnf에

<br>

[client]

<br>

socket=/usr/lib/mysql/mysql.sock추가
 
 
<br>

<img  src="/assets/images/bi11.jpg">






실행완료




