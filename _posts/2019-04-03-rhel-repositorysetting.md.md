---
layout: post
title:  "레드햇 repository 설정"
date:   2019-04-3 11:15:00
author: uni
categories: Rinux Redhat rhel repostitory
cover:  "/assets/header_image5.png"
---


Local Repository 만들기<br>
 

yum repostitory 만들기<br>

rhel-server-7.6-x86_64-dvd  yum setting<br>

cd 나 iso를 읽게 한다 <br>
lsblk 로 확인가능
 
 
 
 <img  src="/assets/images/rp1.jpg">
 
 
 
sr0에 4.2 G <br>

mount 폴더 생성
<br>


 <img  src="/assets/images/rp2.jpg">
 


mount /dev/sr0 /root/iso<br>
 
 
 
 <img  src="/assets/images/rp3.jpg">




cd /etc/yum.repos.d<br>
ls
 

 
 <img  src="/assets/images/rp4.jpg">




cat yum.repos.d<br>

vi redhat.repo<br>
해서 추가<br>
[local-repo]<br>
name=Local Repository<br>
baseurl=file:///root/iso<br>
enabled=1<br>
gpgcheck=0<br>

 
 
 <img  src="/assets/images/rp5.jpg">




yum update 후<br>
rpm -qa | grep yum  로 확인

 


 
 <img  src="/assets/images/rp6.jpg">





자동마운트

vi /etc/fstab

/dev/sr1 /root/iso iso9660 defaults 1 0




 






