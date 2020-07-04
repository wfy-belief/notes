## 关于

---

资料以及内容由小组成员共同完成（不分先后，自行查看贡献度）。

王飞宇 [GitHub](https://github.com/wfy-belief)  王纯 [GitHub](https://github.com/fs86749)  宋景霖 [GitHub](https://github.com/GGsjl) 李世龙 [GitHub](https://github.com/lsl575999)

---



## 维护说明


**<font color=red>2020.5.31</font> 维护**

- 增加 [无法连接远程Linux数据库解决方法](https://github.com/wfy-belief/group-study/blob/master/MySQL/%E6%97%A0%E6%B3%95%E8%BF%9E%E6%8E%A5%E8%BF%9C%E7%A8%8BLinux%E6%95%B0%E6%8D%AE%E5%BA%93%E8%A7%A3%E5%86%B3%E6%96%B9%E6%B3%95.md) 文档
- 增加 [Python操作MySQL数据库](https://github.com/wfy-belief/group-study/blob/master/MySQL/Python%E6%93%8D%E4%BD%9CMySQL%E6%95%B0%E6%8D%AE%E5%BA%93.md) 文档


---

**<font color=red>2020.5.30</font> 维护**

- 增加 `基础查询` `条件查询` `排序查询` `常见函数` 四个板块.
- 修改小组仓库[README.md](https://github.com/wfy-belief/group-study)文档
- 修改小组仓库MySQL目录下[README.md](https://github.com/wfy-belief/group-study/blob/master/MySQL/README.MD)
- 发布小组文档 https://wfyblog.cn/notes/#/group/MySQL
- 发布Wiki书籍https://github.com/wfy-belief/group-study/wiki/MySQL

---



## MySQL——linux安装

完整的纯净系统 系统版本 **Ubuntu 18.02**

换源

```
# 首先备份源列表
cp /etc/apt/sources.list /etc/apt/sources.list_backup
```

```
# 打开sources.list文件
vim /etc/apt/sources.list
```

编辑**/etc/apt/sources.list**文件, 在文件最前面添加阿里云镜像源：

```text
#  阿里源
deb http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
```

刷新

```
apt-get update
apt-get upgrade
```

出现警告

```
Reading package lists... Done
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
```

执行下面命令关闭进程

```
rm /var/lib/apt/lists/lock
```

依次执行刷新命令 

安装

```
sudo apt-get install mysql-server -y
```

## 增删改查

显示数据库

```
show databases
```

使用库

```
use
```

显示表

```
show tables;
```

```
show tables from mysql;
```

查看自己所在库

```
select database();
```

创建数据库

```
create database test;
```

创建表

```
create table stuinfo(
    -> id int,
    -> name  varchar(20));
```

查看表信息

```
desc stuinfo;
```

查看表数据

```
select * from stuinfo;
```

插入数据

```
insert into stuinfo (id, name) values(54100000, 'Tom');
```

修改信息

```
update stuinfo set name='TOM' where id=54100000;
```

删除

```
delete from  stuinfo where id=4411;
```

查看版本信息；

```
select version();
```

退出数据库

```
exit 或者 quit
```

## 基础查询

/*
select 查询列表 from  表名;

特点：
1、查询列表可以是：表中的字段、常量值、表达式、函数
2、查询的结果是一个虚拟的表格
*/

```sql
USE myemployees;
```

#1.查询表中的单个字段

```sql
SELECT last_name FROM employees;
```

#2.查询表中的多个字段

```sql
SELECT last_name,salary,email FROM employees;
```

#3.查询表中所有字段

```sql
SELECT * FROM employees;
```

#4.查询常量值

```sql
SELECT 100;
SELECT 'john';
```

#5.查询表达式

```sql
SELECT 100%98
```

#6.查询函数

```sql
SELECT ABS(-10);
```

#7.起别名
/*
①便于理解
②如果要查询的字段有重名的情况，使用别名可以区分开来

as可以换成空格
*/

```sql
SELECT 100%98 AS 结果;
SELECT last_name AS 姓,first_name AS 名 FROM employees;
```

#案列：查询salary，显示结果位 out put

```sql
SELECT salary AS "out put" FROM employees;
```

#8.去重
#关键字distinct

#案例:查询员工表中涉及到的所有的部门编号

```sql
SELECT DISTINCT department_id FROM employees;
```

#9.+的作用

/*
java中的+
1.运算符 1+1
2.连接符 str+str

mysql中的+
只有运算符功能

```sql
select 100+90; #190 两个操作数都是数值型，做加法运算*
select '123'+90; #213 其中一个位字符型，试图将字符型装换成数值型，若成功，则继续做加法运算
select 'join'+90; #90 如果失败，则将字符型数值转换成0
select null+10; #null 只要其中一方为null，则结果一定是null
```

*/
#案例：查询员工名和姓连接成一个字段，并显示为姓名

```sql
SELECT CONCAT(last_name,first_name) AS 姓名 FROM employees;
```



## 条件查询

#进阶2 条件查询
/*

语法：
	select
		查询列表
	from
		表名
	where
		筛选条件;

分类：
	一、按条件表达式筛选
	条件运算符：> < = !=(<>) >= <=
	

	二、按逻辑表达式筛选
	逻辑运算符：&& || !
		    and or not(都可)
	逻辑运算符作用：用于连接条件表达式
	
	三、模糊查询
		like
		between and
		in
		is null

*/

#一、按条件表达式筛选

#案例1：查询员工工资>12000的员工信息

```sql
SELECT
	*
FROM
	employees
WHERE
	salary>12000;
```

#案例2:查询部门编号不等于90号的员工名和部门编号

```sql
SELECT
	last_name,
	department_id
FROM
	employees
WHERE
	department_id <> 90;
```


​	
#二、按逻辑表达式筛选

#案例1：工资在1w到2w之间的员工名、工资以及奖金

```sql
SELECT
	last_name,
	salary,
	commission_pct
FROM
	employees
WHERE
	salary >= 10000 AND salary <= 20000
```

#案例2：查询部门编号不是在90到110之间，或者工资高于15000的员工信息

```sql
SELECT
	*
FROM
	employees
WHERE
	department_id < 90 OR department_id > 110 OR salary > 15000;
```


​	
#三、模糊查询
/*
like
特点：
1.一般和通配符搭配使用
​	通配符
​		%任意多个字符，包含0个字符
​		_任意单个字符

between and
in
is null | is not null;

*/

#1.like

#案例1:查询员工名中包含字符a的员工信息

```sql
SELECT
	*
FROM
	employees
WHERE
	last_name LIKE '%a%';
```

#案例2:查询员工名中第三个字符为n,第五个字符为l的员工名和工资

```sql
SELECT
	last_name,
	salary
FROM
	employees
WHERE
	last_name LIKE '__n_l%';
```

#案例3

```sql
#案例3:查询员工名中第二个字符为_的员工名     escape转义_
SELECT
	last_name
FROM
	employees
WHERE
	last_name LIKE '_$_%' ESCAPE '$';
```

#2.between and
/*
①使用betweenand可以提高语句的简洁度
②包含临界值
③两个临界值不要调换顺序

*/

#案例1:查询员工编号在100到120之间的员工信息

```sql
SELECT
	*
FROM
	employees
WHERE
	employee_id BETWEEN 100 AND 120;#employee_id >= 100 AND employee_id <= 120
```

#3.in  反之就是not in

含义:判断某字段的值是否属于in列表中的某一项
特点：
	①使用in提高语句简介度
	②in列表的值类型必须一致或兼容(123 '123')
	③in列表里面不能使用通配符

#案例:查询员工的工种编号是IT_PROG、 AD_VP、 AD_PRES中的一个的员工名和工种编号

```sql
SELECT
	last_name,
	job_id
FROM
	employees
WHERE
	job_id IN('IT_PROG', 'AD_VP', 'AD_PRES'); #job_id = 'IT_PROG' or job_id = 'AD_VP' or job_id='AD_PRES';
```

#4.is null/is not null

=或<>不能 用于判断null值
is null或is not null可以判断null值



#案例1:查询没有奖金的员工名和奖金率

```sql
SELECT
	last_name,
	commission_pct
FROM
	employees
WHERE
	commission_pct IS NOT NULL;
```

​	

#安全等于  <=>

#案例1:查询没有奖金的员工名和奖金率

```sql
SELECT
	last_name,
	commission_pct
FROM
	employees
WHERE
	commission_pct <=> NULL;
```

#案例2:查询工资为12000的员工信息

```sql
SELECT
	last_name,
	salary
FROM
	employees
WHERE
	salary <=> 12000;
```

#is null vs <=>

#IS NULL:仅仅可以判断NULL值，可读性较高，建议使用
#<=>：既可以判断NULL值，又可以判断普通的数值，可读性较低

## 排序查询

#进阶3：排序查询

/*

语法：
	select	查询列表
	from	表
	【where	筛选条件】
	order by 排序列表【asc|desc】（升|降）默认asc

特点:
	1.asc是升序，desc是降序
	2.order by可以支持单个字段或者多个字段按照不同的方式排序
	3.order by子句一般是放在查询语句的最后面（limit子句除外）
	
*/

```sql
USE myemployees;
```

#案例1:查询员工信息，要求工资从高到低排序

```sql
SELECT
	*

FROM
	employees
ORDER BY	salary DESC;
```

#案例2:查询部门编号>=90的员工信息，按入职时间的先后进行排序

```sql
SELECT
	*
FROM
	employees
WHERE
	department_id >= 90
ORDER BY hiredate;
```

#案例3:按年薪的高低显示员工的信息和年薪[按表达式排序]

```sql
SELECT
	*,
	salary*12*(1+IFNULL(commission_pct,0)) AS 年薪
FROM
	employees
ORDER BY salary*12*(1+IFNULL(commission_pct,0)) DESC;
```

#案例4:按年薪的高低显示员工的信息和年薪[按别名排序]

```sql
SELECT
	*,
	salary*12*(1+IFNULL(commission_pct,0)) AS 年薪
FROM
	employees
ORDER BY 年薪 DESC;
```

#案例5:按姓名的长度显示员工的姓名和工资[ 按函数排序]

```sql
SELECT
	LENGTH(last_name) AS 字节长度,
	last_name,
	salary
FROM
	employees
ORDER BY LENGTH(last_name) DESC;
```

#案例6:查询员工信息，要求先按工资排序，再按员工编号排序[按多个字段排序]

```sql
SELECT	*
FROM	employees
ORDER BY salary ASC, employee_id DESC;
```

## 常见函数

#进阶4：常见函数

/*

调用：select 函数名(实参列表) 【from 表】;
特点：
	①函数名（叫什么）
	②函数功能（干什么）

分类：
	1.单行函数
	如concat、length、ifnull等
	2.分组处理（统计函数）

*/

#一、字符函数

#1.length 获取参数值的字节个数，中文3个，英文1个

```sql
SELECT LENGTH('我你');
```

#2.concat 拼接函数

```sql
SELECT CONCAT(last_name,'_',first_name) FROM employees;
```

#3.upper,lower

```sql
SELECT UPPER('aADsjd');
SELECT LOWER('asdASD');
```

#示例:将姓变大写，名变小写，然后拼接

```sql
SELECT CONCAT(UPPER(last_name),'_',LOWER(first_name)) AS 姓名 FROM employees;
```

#4.substr、substring 截取
#索引从1开始

#截取从指定索引处后面所有字符

```sql
SELECT SUBSTR('asdas', 3);
```

#截取从指定索引处指定字符长度的字符

```sql
SELECT SUBSTR('asdas', 1, 3);
```

#案例:姓名中首字符大写，其他字符小写然后用_拼接，显示出来

```sql
SELECT CONCAT(UPPER(SUBSTR(last_name,1,1)), LOWER(SUBSTR(last_name,2)), '_', LOWER(first_name)) AS 姓名 FROM employees;
```

#5.instr
#返回起始索引，如果找不到返回0

```sql
SELECT INSTR('阿珍爱上了阿强', '阿强') AS print;
```

#6.trim
#去除字符串前后指定东西，默认是空格

```sql
SELECT LENGTH(TRIM('    阿珍爱上了阿强    ')) AS print;
SELECT TRIM('a' FROM 'aaaaaaaaaa阿a珍a爱a上a了a阿aaaaa强aaaaaaaaaa') AS print;
```

#7.lpad
#用指定字符实现左填充指定长度

```sql
SELECT LPAD('阿强', 10, '*') AS print;
```

#8.rpad
#用指定字符实现左填充指定长度

```sql
SELECT RPAD('阿强', 10, '*') AS print;
```

#9.repalce

```sql
SELECT REPLACE('阿珍爱上了阿强阿强阿强', '阿强', '阿宝') AS print;
```
