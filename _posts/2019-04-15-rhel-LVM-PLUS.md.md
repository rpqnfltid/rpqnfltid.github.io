---
layout: post
title:  "레드햇 LVM 용량 추가"
date:   2019-04-15 11:33:00
author: uni
categories: Rinux Redhat rhel LVM
cover:  "/assets/header_image5.png"

---


  20GB의 하드디스크를 1개 더 추가한다.<br>
    추가한 하드디스크는 아래와 같은 파티션으로 구성한다.<br>
a.     10GB의 용량을 가지는 볼륨그룹 VG01 생성 후<br>
b.  LV01 10GB<br>
  LV01를 10GB->20GB<br>
 
10GB를 추가  용량 증설<br>
20GB만들기<br>
실제마운트 df로 mount가 20GB<br>


<br>
 fdisk /dev/sdb<br>
fdisk /dev/sdc<br>

n<br>
p<br>
1<br>
1<br>
+10GB<br>
T<br>
8e<br>
W<br>
<br>



vgcreate VG01 /dev/sdb1<br>
 <br>
lvcreate -l 100%FREE -n lv01 VG01<br>
 <br>
vgextend VG01 /dev/sdc1<br>
 <br>
lvcreate -l +100%FREE -n LV01 /dev/VG01<br>
 <br>
lvextend /dev/VG01/LV01 -l  +100%FREE<br>
 <br>
rhgel5 확인방법 fdsik -l<br>
rhel 6은 fdisk Dm-@<br>
 <br>
 <br>
mkfs -t ext2 /dev/dm-2<br>
 <br>
resize2fs /dev/VG01/LV01<br>
 <br>
mount /dev/dm-2 /root<br>
 <br>

df -T -h  확인






 
 