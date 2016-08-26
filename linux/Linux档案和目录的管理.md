## Linux档案和目录管理
> #### 目录相关操作  
> 1、  '.' 代表此层目录  
  2、 '..' 代表上层目录  
  3、 '-' 代表前一个工作目录  
  4、 '~' 代表目前用户所在的home目录  
  5、 ‘~account' 代表account这个用户所在的home目录   

---

> #### 常见的处理目录的指令
> 1、cd 变换目录  
  2、pwd 显示当前目录  
  3、mkdir 建立一个新的目录  
  4、rmdir 删除一个空的目录<br>  
> <em style="font-size: 16px">cd</em>  
  [root@wangjie ~]# cd [相对路径或者绝对路径]<br>  
> <em style="font-size: 16px">pwd</em>   
  [root@www ~]# pwd [-P]  
   -P :显示出确实癿路径,而非使用链接 (link) 路径<br>   
> <em style="font-size: 16px">mkdir</em>  
    mkdir [-mp] 目录名称  
    -m :配置文件目录权限!直接设定,不需要看预设权限 (umask) 的脸色~  
    -p :帮你直接将所需要的目录(包含上层目录)递归建立起来!  
    例:  
    [root@wangjie tmp]# mkdir test  
    [root@wangjie tmp]# mkdir -p test1/test2/test3/test4  
    [root@wangjie tmp]# mkdir -m 711 test2<br>  
> <em style="font-size: 16px">rmdir</em>  
  [root@wangjie ~]# rmdir [-p] 目录名称  
   -p :连同上层『空的』目录也一起删除  
   注：这个 rmdir 仅能『删除空的目录』喔!

---

> #### 档案与目录的管理<br>
> <em style="font-size: 16px">档案与目录的检视 ls</em>  
  [root@wangjie ~]# ls [-aAdfFhilnrRSt] 目录名称  
  [root@wangjie ~]# ls [--color={never,auto,always}] 目录名称  
  [root@wangjie ~]# ls [--full-time] 目录名称  
  -a :全部的档案,连同隐藏档( 开头为 . 的档案) 一起列出来(常用)    
  -A :全部的档案,连同隐藏档,但不包括 . 与 .. 这两个目录  
  -d :仅列出目录本身,而不是列出目录内档案案数据(常用) 
  -l :长数据串行出,包括档案的属性与权限等等数据;(常用)   
  -f :直接列出结果,而不进行排序 (ls 预设会以档名排序!)        
  -F :根据档案、目录等信息,给予附加数据结构,例如:  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*:代表可执行文件; /:代表目录; =:代表 socket 档案; |:代表 FIFO 档案;  
  -h :将档案容量以人类较易读的方式(例如 GB, KB 等等)列出来  
  -i :列出 inode 号码  
  -n :列出 UID 与 GID 而非使用者与群组的名称  
  -r :将排序结果反向输出,例如:原本档名由小到大,反向则为由大到小  
  -R :连同子目录内容一起列出来,等于该目录下的所有档案都会显示出来    
  -S :以档案容量大小排序,而不是用档名排序  
  -t :依时间排序,而不是用档名   
  --color=never :丌要依据档案特性给予颜色显示  
  --color=always :显示颜色  
  --color=auto :该系统自行依据设定来判断是否给予颜色  
  --full-time:以完整时间模式 (包扩年、月、日、时、分) 输出  
  --time={atime,ctime} :输出 access 时间或改变权限属性时间 (ctime)而非内容变更时间 (modification time)<br>  
> <em style="font-size: 16px">复制档案或目录  cp</em>  
  [root@wangjie ~]# cp [-adfilprsu] 来源文件(source) 目标文件(destination)  
  [root@wangjie ~]# cp [options] source1 source2 source3 .... directory
  
  
  

