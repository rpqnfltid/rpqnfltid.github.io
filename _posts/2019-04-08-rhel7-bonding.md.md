---
layout: post
title:  "레드햇 bonding 설정"
date:   2019-04-8 9:25:00
author: uni
categories: Rinux Redhat rhel bonding
cover:  "/assets/header_image5.png"

---


 <br>
 
 

cd /etc/sysconfig/network-scripts/<br>

<br>
본드0 만들기<br><br>
ifcfg-bond0<br>

 
 
 
 

vi ifcfg-bond0<br><br><br>

DEVICE=bond0<br>
NAME=bond0<br>
TYPE=Bond<br>
BONDING_MASTER=yes<br>


IPADDR=192.168.0.2<br>
NETMASK=255.255.255.0<br>
GATEWAY=192.168.1.1<br>

PREFIX=24<br>
ONBOOT=yes<br>
BOOTPROTO=none<br>
BONDING_OPTS="mode=1 miimon=100"<br><br>



 <img  src="/assets/images/bon1.jpg"><br>
 
<br><br>

vi ifcfg-ens33<br><br>

DEVICE=ens33<br>
NAME=bond0-slave<br>
TYPE=Ethernet<br>
BOOTPROTO=none<br>
ONBOOT=yes<br>
MASTER=bond0<br>
SLAVE=yes<br>

 


 
 
 <img  src="/assets/images/bon2.jpg">
 
 



vi ifcfg-ens34<br>



 
 
 <img  src="/assets/images/bon3.jpg"><br>
 
 

 



Service network restart <br>



 
 
 
 <img  src="/assets/images/bon4.jpg"><br>
 
 








