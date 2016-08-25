## Mysql表连接
#### 一、 表结构如下
> <span>1、 R表</span> <table border="2" width=200px style="text-align: center"><tr><th>A</th><th>B</th><th>C</th></tr><tr><td>a1</td><td>b1</td><td>c1</td></tr><tr><td>a2</td><td>b2</td><td>c2</td></tr><tr><td>a3</td><td>b3</td><td>c3</td></tr> </table>
> 2、S表 <table border="2" width=200px style="text-align: center;"><tr><th>C</th><th>D</th></tr><tr><td>c1</td><td>d1</td></tr><tr><td>c2</td><td>d2</td></tr><tr><td>c3</td><td>d3</td></tr></table>
> &nbsp;

#### 二、 表连接方式
> #### 笛卡尔积 
> mysql> select* from S,R;  <table width=80% border="2" style="text-align:center; min-width: 400px; max-width: 800px">
    <tr><th>A</th><th>B</th><th>C</th><th>C</th><th>D</th></tr>
    <tr><td>a1</td><td>b1</td><td>c1</td><td>c1</td><td>d1</td></tr>
    <tr><td>a1</td><td>b1</td><td>c1</td><td>c2</td><td>d2</td></tr>
    <tr><td>a1</td><td>b1</td><td>c1</td><td>c3</td><td>d3</td></tr>
    <tr><td>a2</td><td>b2</td><td>c2</td><td>c1</td><td>d1</td></tr>
    <tr><td>a2</td><td>b2</td><td>c2</td><td>c2</td><td>d2</td></tr>
    <tr><td>a2</td><td>b2</td><td>c2</td><td>c3</td><td>d3</td></tr>
    <tr><td>a3</td><td>b3</td><td>c3</td><td>c1</td><td>d1</td></tr>
    <tr><td>a3</td><td>b3</td><td>c3</td><td>c2</td><td>d2</td></tr>
    <tr><td>a3</td><td>b3</td><td>c3</td><td>c3</td><td>d3</td></tr>
    </table>
    &nbsp; 注： 不需要任何条件，结果为两张表相乘（3*3=9)  
    <b>自连接</b>   
  mysql> select m.A,m.B,m.C,n.A,n.B,n.C from R m,R n where m.A=n.A;  <table width=80% border="2" style="text-align:center; min-width: 400px; max-width: 800px">
    <tr><th>A</th><th>B</th><th>C</th><th>A</th><th>B</th><th>C</th></tr>
    <tr><td>a1</td><td>b1</td><td>c1</td><td>a1</td><td>b1</td><td>c1</td></tr>
    <tr><td>a2</td><td>b2</td><td>c2</td><td>a2</td><td>b2</td><td>c2</td></tr>
    <tr><td>a3</td><td>b3</td><td>c3</td><td>a3</td><td>b3</td><td>c3</td></tr>
    </table>
    &nbsp;


> ### 连接类型  
> 分为三种: 交叉连接、内连接、外连接  


> #### <em>交叉连接 cross join</em>  
> mysql> select * from R cross join S;  
    没有任何筛选条件的交叉连接是两张表的笛卡尔积  <table width=80% border="2" style="text-align:center; min-width: 400px; max-width: 800px">
        <tr><th>A</th><th>B</th><th>C</th><th>C</th><th>D</th></tr>
        <tr><td>a1</td><td>b1</td><td>c1</td><td>c1</td><td>d1</td></tr>
        <tr><td>a1</td><td>b1</td><td>c1</td><td>c2</td><td>d2</td></tr>
        <tr><td>a1</td><td>b1</td><td>c1</td><td>c3</td><td>d3</td></tr>
        <tr><td>a2</td><td>b2</td><td>c2</td><td>c1</td><td>d1</td></tr>
        <tr><td>a2</td><td>b2</td><td>c2</td><td>c2</td><td>d2</td></tr>
        <tr><td>a2</td><td>b2</td><td>c2</td><td>c3</td><td>d3</td></tr>
        <tr><td>a3</td><td>b3</td><td>c3</td><td>c1</td><td>d1</td></tr>
        <tr><td>a3</td><td>b3</td><td>c3</td><td>c2</td><td>d2</td></tr>
        <tr><td>a3</td><td>b3</td><td>c3</td><td>c3</td><td>d3</td></tr>
        </table>  
    加入<b><em>where</em></b>筛选条件  
    mysql> select * from R cross join S where R.C = S.C;   
        &nbsp;
        <table width=80% border="2" style="text-align:center;min-width: 400px; max-width: 800px">
        <tr><th>A</th><th>B</th><th>C</th><th>C</th><th>D</th></tr>
        <tr><td>a1</td><td>b1</td><td>c1</td><td>c1</td><td>d1</td></tr>
        <tr><td>a2</td><td>b2</td><td>c2</td><td>c2</td><td>d2</td></tr>
        <tr><td>a3</td><td>b3</td><td>c3</td><td>c3</td><td>d3</td></tr>
        </table>  
> #### <em>内连接</em>  
> 内连接分为三种：自然连接、等值连接、非等值连接   
    &nbsp;  
    <em>自然连接 natural join</em>: 自动对两个表按照同名的列进行内连接  
    mysql>  select * from R natural join S; <table width=80% border="2" style="text-align:center;min-width: 400px; max-width: 800px">
        <tr><th>A</th><th>B</th><th>C</th><th>D</th></tr>
        <tr><td>a1</td><td>b1</td><td>c1</td><td>d1</td></tr>
        <tr><td>a2</td><td>b2</td><td>c2</td><td>d2</td></tr>
        <tr><td>a3</td><td>b3</td><td>c3</td><td>d3</td></tr>
    </table>  <br> 
    <em>等值连接</em>: 使用等于=比较连接列的列值，在查询结果钟列出连接表中所有的列,包括其中重复的列<br> 
    mysql> select * from R join S where R.C = S.C; <table width=80% border="2" style="text-align:center;min-width: 400px; max-width: 800px">
        <tr><th>A</th><th>B</th><th>C</th><th>C</th><th>D</th></tr>
        <tr><td>a1</td><td>b1</td><td>c1</td><td>c1</td><td>d1</td></tr>
        <tr><td>a2</td><td>b2</td><td>c2</td><td>c2</td><td>d2</td></tr>
        <tr><td>a3</td><td>b3</td><td>c3</td><td>c3</td><td>d3</td></tr>
        </table> <br>
    mysql> mysql> select * from R,S where R.C = S.C; <table width=80% border="2" style="text-align:center;min-width: 400px; max-width: 800px">
        <tr><th>A</th><th>B</th><th>C</th><th>C</th><th>D</th></tr>
        <tr><td>a1</td><td>b1</td><td>c1</td><td>c1</td><td>d1</td></tr>
        <tr><td>a2</td><td>b2</td><td>c2</td><td>c2</td><td>d2</td></tr>
        <tr><td>a3</td><td>b3</td><td>c3</td><td>c3</td><td>d3</td></tr>
        </table> <br>
    <em>非等值连接</em>: 在连接条件中,可以使用其他的比较运算符，如:<、>、!=等<br><br>
> #### <em>外连接 cross join</em>
> 外连接分为三类：全外连接、左外连接、右外连接<br>
    R表</span> <table border="2" width=200px style="text-align: center"><tr><th>A</th><th>B</th><th>C</th></tr><tr><td>a1</td><td>b1</td><td>c1</td></tr><tr><td>a2</td><td>b2</td><td>c2</td></tr><tr><td>a3</td><td>b3</td><td>c3</td></tr> </table>  
    mysql> update S set C = 'c4' where D = 'd3';  
    S表 <table border="2" width=200px style="text-align: center;"><tr><th>C</th><th>D</th></tr><tr><td>c1</td><td>d1</td></tr><tr><td>c2</td><td>d2</td></tr><tr><td>c4</td><td>d3</td></tr></table>
    <br><em>左外连接  left join / left outer join<em><br>
    mysql> select * from R left join S on R.C = S.C; <table width=80% border="2" style="text-align:center;min-width: 400px; max-width: 800px">
        <tr><th>A</th><th>B</th><th>C</th><th>C</th><th>D</th></tr>
        <tr><td>a1</td><td>b1</td><td>c1</td><td>c1</td><td>d1</td></tr>
        <tr><td>a2</td><td>b2</td><td>c2</td><td>c2</td><td>d2</td></tr>
        <tr><td>a3</td><td>b3</td><td>c3</td><td>null</td><td>null</td></tr>
    </table><br>
    <em>右外连接 right join / right outer join<em>  
    mysql>  select * from R right join S on R.C = S.C;<table width=80% border="2" style="text-align:center;min-width: 400px; max-width: 800px">
        <tr><th>A</th><th>B</th><th>C</th><th>C</th><th>D</th></tr>
        <tr><td>a1</td><td>b1</td><td>c1</td><td>c1</td><td>d1</td></tr>
        <tr><td>a2</td><td>b2</td><td>c2</td><td>c2</td><td>d2</td></tr>
        <tr><td>null</td><td>null</td><td>null</td><td>c4</td><td>d3</td></tr>
    </table><br>
    <em> 全外连接 full join / full outer join<em>  
    mysql> select * from R full join S on R.C=S.C  
    or  
    mysql> seselect * from R left join S on R.C=S.C  
    union  
    select * from R right join S on S.C=R.C;<table width=80% border="2" style="text-align:center;min-width: 400px; max-width: 800px">
        <tr><th>A</th><th>B</th><th>C</th><th>C</th><th>D</th></tr>
        <tr><td>a1</td><td>b1</td><td>c1</td><td>c1</td><td>d1</td></tr>
        <tr><td>a2</td><td>b2</td><td>c2</td><td>c2</td><td>d2</td></tr>
        <tr><td>a3</td><td>b3</td><td>c3</td><td>null</td><td>null</td></tr>
        <tr><td>null</td><td>null</td><td>null</td><td>c4</td><td>d3</td></tr>
    </table><br>

   






    





  











