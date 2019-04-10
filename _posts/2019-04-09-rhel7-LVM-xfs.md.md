---
layout: post
title:  "레드햇 LVM xfs 설정"
date:   2019-04-09 17:37:00
author: uni
categories: Rinux Redhat rhel LVM xfs filesystem
cover:  "/assets/header_image5.png"

---


<h3>

 

 
LVM <br><br>



    1 20GB의 하드디스크를 1개 더 추가한다. <br>
     추가한 하드디스크는 아래와 같은 파티션으로 구성한다. <br>
  a   10GB의 용량을 가지는 볼륨그룹 VG01 생성<br>
  b  10GB의 용량을 가지는 볼륨그룹 VG02 생성<br>
  c   VG01에 5GB의 용량을 가지는 LV01 생성<br>
  d  VG01에 5GB의 용량을 가지는 LV02 생성<br>
  e   VG02에 3GB의 용량을 가지는 LV03 생성<br>
   f   VG02에 3GB의 용량을 가지는 LV04 생성<br>
  g  VG02에 4GB의 용량을 가지는 LV05 생성<br>
  2   LV01과 LV02는 xfx 파일시스템으로 포맷한다. <br>
  3   LV03~05는 ext4 파일시스템으로 포맷한다   <br>
  LV01은 /lvdir01 LV02는 /lvdir02에 각각 영구 마운트한다. <br>

<br>
yum install lvm2* -y<br><br>

 


 
 <img  src="/assets/images/lvm1.jpg"><br>
 
 

 
lsblk<br>
fdisk /dev/sdc <br>

N<br>
default<br>
default<br>
default<br>
+10G<br>
N<br>
default<br>
default<br>
default<br>
default<br>
w<br>

 

 
 <img  src="/assets/images/lvm2.jpg"><br><br>
 
 

 


vgcreate VG01 /dev/sc1<br>
vgcreate VG02 /dev/sc2<br>
 


 
 <img  src="/assets/images/lvm3.jpg"><br>
 
 

 

lvcreate -L 5G -n LV01 VG01<br>
lvcreate -l 1279 -n LV02 VG01<br>
lvcreate -L 5G -n LV03 VG02<br>
lvcreate -L 5G -n LV04 VG02<br>
lvcreate -l 1023 -n LV05 VG02<br>

 

 
 <img  src="/assets/images/lvm4.jpg"><br><br>
 
 

 

yum install xfs*<br><br>

mkfs  -t   xfs -f /dev/VG01/LV01<br>
mkfs  -t   xfs -f /dev/VG01/LV02<br><br>
 

 
 <img  src="/assets/images/lvm5.jpg"><br>
 
 

 

mkfs -t  ext4  /dev/VG02/LV03<br>
mkfs -t  ext4  /dev/VG02/LV04<br><br>
mkfs -t  ext4  /dev/VG02/LV05<br>
 


 
 <img  src="/assets/images/lvm6.jpg"><br>
 
 

 

mkdir /lvdir01<br>
mkdir /lvdir02<br>
mount /dev/VG01/LV01 /lvdir01<br>
mount /dev/VG01/LV02 /lvdir02<br><br>

 




 
 <img  src="/assets/images/lvm7.jpg"><br>
 
 

 





</h3>
<br>

Vi /etc/fstab<br>

/dev/VG01/LV01 /lvdir01 xfs defaults 1 0<br>
/dev/VG01/LV02 /lvdir02 xfs defaults 1 0<br>
 



 
 <img  src="/assets/images/lvm8.jpg"><br><br>
 
 </h3>
















 
 <br>