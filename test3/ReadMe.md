# 实验三：图书管理系统领域对象建模
<table>
<tr>
<td>学号</td>
<td>班级</td>
<td>姓名</td>
</tr>
<tr>
<td>201510414229</td>
<td>15软工2班</td>
<td>周鑫</td>
</tr>
</table>

### 1.图书管理系统的类图

1.1 PlantUml源码如下:
```$xslt
@startuml
class 馆藏目录{
    文献编号
    文献信息
}
class 馆藏资源品种{
    资源名称
    国际出版号
    价格
    简介
    馆藏数量
    可借数量
}
class 图书品种{
    作者
    出版社
    出版日期
}
class 预定记录{
    预定日期
    预定书号
}
class 资源项{
    馆藏流水号
    状态
}
class 借书记录{
    借书日期
    归还日期
}
class 读者{
    姓名
    身份证号
    借书卡号
    图书限额
    已借图书数
}
class 图书管理员{
    职工名
    姓名
}
class 逾期记录{
    逾期天数
}
class 罚款规则{

}
馆藏目录 "1" - "1..*" 馆藏资源品种
馆藏资源品种 "1" *- "*" 资源项 :    拥有
预定记录 "*" -- "1"馆藏资源品种 : 被预定
馆藏资源品种 <|-- 图书品种
预定记录 "*" -- "1" 读者
资源项 "1" -- "0..1"借书记录
图书管理员 "1" - "*" 借书记录 : 登记
借书记录 "*" - "1" 读者
借书记录 "1" --  "0..1" 逾期记录
逾期记录 "*" - "0..1" 罚款规则 : 使用
@enduml
```
1.2 类图如下:

![](./class.png '图1')

1.3 类图说明:

馆藏目录：这个类的属性包括文献编号，文献名，文献信息等属性。可通过此类查询图书馆是否有此类图书。由实列维护书目产生，由维护书目和查询书目等实列应用。<br>
馆藏资源品种：这个类的属性包括资源名称，国际出版号，价格，馆藏数量，可借数量等。由实列维护书目产生，由维护书目和查询书目等实列应用。<br>
资源项：这个类的属性包括馆藏流水号，状态（状态有借出，未借出）等。由实列借出图书，归还图书产生，由归还图书等实列应用。<br>
预定记录：这个类的属性包括预定日期等。由实列预定图书产生，由实列取消预定应用。由实列维护书目产生，由实列预定图书产生，由实列维护书目产生，由维护书目借出图书，归还图书和预定图书等实列应用。<br><
读者：这个类的属性不同 名，身份证号，借书卡号，图书限额，有借图书数，碟片限额，已借碟片数等。由实列维护读者信息产生，由借出图书，归还图书，预定图书，修改密码和维护读者信息等实列应用。<br>
图书管理员：这个类的属性包括职工号，姓名等。由实列维护图书管理员信息产生，由维护图书管理员信息和修改密码等实列应用。<br>
逾期记录：这个类的属性包括逾期天数，由于实列借出图书和归还图书产生，由实列归还图书应用。<br>
罚款细则：这个类的属性包括逾期天数，罚款规则等。当罚款金额超过图书售价，罚款金额将不再随时间增长。<br>

### 2.图书管理系统的对象图

##### 2.1 类借书记录的对象图

源码如下：
```
object 借书记录{

    借书卡号="20151041"
    书籍ISBN号="979-976-987-345-2"
    借书日期="2011-09-09"
    应还日期="2011-10-09"
    还书日期="2011-09-28"
}
```
对象图如下：

![](./借书记录.png  '图2')

##### 2.2类图书品种的对象图

源码如下：
```
object 图书品种{

    ISBN号="979-979-643-234-2"
    书名="oracle数据库"
    作者="赵卫东"
    出版社="电子科技大学出版社"
    馆藏量="200"
    可借量="100"
}
```
对象图如下：

![](./图书品种.png  '图2')

##### 2.3类图书管理员的对象图

源码如下：
```

object administer{

    职工号="1111"
    姓名="zzz"
}
```
对象图如下：

![](./administer.png  '图3')


##### 2.4类读者的对象图

源码如下：
```
object 读者{
    姓名="zx"
    借书卡号="111"
    借出限额="11"
    可用限额="1"
}
```
对象图如下：

![](./reader.png  '图4')

##### 2.5类预定记录的对象图

源码如下：
```
object 预订记录{

    借书卡号="20151041"
    书籍ISBN="987-979-231-232-4"
    预订日期="2014-11-21"
}
```
对象图如下：

![](./预订记录.png  '图5')


