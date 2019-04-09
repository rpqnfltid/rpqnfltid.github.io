---
layout: post
title:  "레드햇 LVM xfs 설정"
date:   2019-04-09 17:37:00
author: uni
categories: Rinux Redhat rhel LVM xfs filesystem
cover:  "/assets/header_image5.png"

---


<h3>
 
 <img  src="/assets/images/swap1.jpg"><br>
 
 

 
LVM 



     20GB의 하드디스크를 1개 더 추가한다. 
     추가한 하드디스크는 아래와 같은 파티션으로 구성한다. 
     10GB의 용량을 가지는 볼륨그룹 VG01 생성
    10GB의 용량을 가지는 볼륨그룹 VG02 생성
     VG01에 5GB의 용량을 가지는 LV01 생성
    VG01에 5GB의 용량을 가지는 LV02 생성
     VG02에 3GB의 용량을 가지는 LV03 생성
      VG02에 3GB의 용량을 가지는 LV04 생성
    VG02에 4GB의 용량을 가지는 LV05 생성
     LV01과 LV02는 xfx 파일시스템으로 포맷한다. 
     LV03~05는 ext4 파일시스템으로 포맷한다   
  LV01은 /lvdir01 LV02는 /lvdir02에 각각 영구 마운트한다. 


yum install lvm2* -y

 


 
 <img  src="/assets/images/swap1.jpg"><br>
 
 

 
lsblk
fdisk /dev/sdc 

N
default
default
default
+10G
N
default
default
default
default
w

 

 
 <img  src="/assets/images/swap1.jpg"><br>
 
 

 


vgcreate VG01 /dev/sc1
vgcreate VG02 /dev/sc2
 


 
 <img  src="/assets/images/swap1.jpg"><br>
 
 

 

lvcreate -L 5G -n LV01 VG01
lvcreate -l 1279 -n LV02 VG01
lvcreate -L 5G -n LV03 VG02
lvcreate -L 5G -n LV04 VG02
lvcreate -l 1023 -n LV05 VG02

 

 
 <img  src="/assets/images/swap1.jpg"><br>
 
 

 

yum install xfs*

mkfs  -t   xfs -f /dev/VG01/LV01
mkfs  -t   xfs -f /dev/VG01/LV02
 

 
 <img  src="/assets/images/swap1.jpg"><br>
 
 

 

mkfs -t  ext4  /dev/VG02/LV03
mkfs -t  ext4  /dev/VG02/LV04
mkfs -t  ext4  /dev/VG02/LV05
 


 
 <img  src="/assets/images/swap1.jpg"><br>
 
 

 

mkdir /lvdir01
mkdir /lvdir02
mount /dev/VG01/LV01 /lvdir01
mount /dev/VG01/LV02 /lvdir02

 




 
 <img  src="/assets/images/swap1.jpg"><br>
 
 

 





</h3>

















 
 