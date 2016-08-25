## Linux 文件属性
> 1.文件属性示意图<br>  
  <img src="img/directory.png" style="background-color: #fff"/>

---

> 2.档案的类型与权限内容<br> 
  <img src="img/powers.png" style="background-color: #fff"/>  
> 档案类型
> + 当为[ d ]则是目录
> + 当为[ - ]则是档案
> + 若是[ l ]则表示为连结档(link file)
> + 若是[ b ]则表示为装置文件里面的可供储存的接口设备(可随机存取装置)
> + 若是[ c ]则表示为装置文件里面的串行端口讴备,例如键盘、鼠标(一次怅读取装置) 

---

> 3.改变文件属性与权限  
  <br>&nbsp;&nbsp;&nbsp;&nbsp;chgrp: 改变档案所属群组
  <br>&nbsp;&nbsp;&nbsp;&nbsp;chown: 改变档案拥有者
  <br>&nbsp;&nbsp;&nbsp;&nbsp;chmod: 改变档案的权限, SUID, SGID, SBIT 等等的特性
  <br><br>
  (1) 改变所属群组 chgrp  
    root@wangjie ~]# chgrp [-R] dirname/filename ...  
    选顷不参数:  
    -R : 进行递归(recursive)的持续变更，即对这个目录下所有文件目录<br>  
  (2) 改变档案拥有者 chown  
    [root@wangjie ~]# chown [-R] 账号名称 档案或目彔  
    [root@wangjie ~]# chown [-R] 账号名称:组名 档案或目彔<br>  
  (3) 改变权限  chmod  
>  + 数字类型改变档案权限  
    r:4  
    w:2  
    x:1  
    root@wangjie ~]# chmod [-R] xyz 档案或目录  
    选顷不参数:  
    xyz : 就是刚刚提到的数字类型的权限属怅,为 rwx 属怅数值的相加。  
    -R : 迚行递归(recursive)的持续变更,亦即连同次目彔下的所有档案都会变更  
    例： chmod 777 档案或目录 
> + 符号类型改变档案权限
    

