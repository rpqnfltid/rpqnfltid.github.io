---
layout: post
title:  "레드햇 root passwd 재설정"
date:   2019-04-8 14:25:00
author: uni
categories: Rinux Redhat rhel root passwd

---

 

 
 
ctrl+alt+del <br>




linux 칸 end키 후 rd.break console=tty1 <br>

 
  <br> <br>
 
 <img  src="/assets/images/rootp1.jpg"><br>
 




ctrl + x <br>


mount -o remonut,rw /sysroot <br>




chroot /sysroot  <br>




passwd root <br>




touch /.autorelabel  <br>





exit  <br>



exit  <br>


 <br>
 
 
 <img  src="/assets/images/rootp2.jpg"><br> <br>
 


  <br>





 
 



