## Linux 环境变量
> #### 执行文件路径变量: $PATH  
> PATH(一定是大写)这个变量的内容是由一堆目录所组成的,每个目录中间用冒号(:)隔开, 每个目录是有『顺序』之分的<br>
  例：  
    [root@www ~]# echo $PATH  
    /usr/kerberos/sbin:/usr/kerberos/bin:/usr/local/sbin:/usr/local/bin:/sbin
    :/bin:/usr/sbin:/usr/bin:/root/bi<br>  
  1、不同身份使用者预设的 PATH 不同,默讣能够随意执行的指令也不同  
  2、 PATH 是可以修改的,所以一般使用者还是可以透 过修改 PATH 来执行某些位于/sbin 或/usr/sbin 下的指令来查询  
  3、 使用绝对路径或相对路径直接指定某个指令的文件名来执行,会比搜寻 PATH 来的正确;  
  4、 指令应该要放置到正确的目录下,执行才会比较方便  
  5、 本目录(.)最好不要放到 PATH 当中  
  