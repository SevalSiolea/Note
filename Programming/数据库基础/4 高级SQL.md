## 一  知识结构

#### 1  使用程序设计语言访问SQL

1.1  JDBC
	1.1.1  连接到数据库
	1.1.2  执行SQL语句
	1.1.3  预备语句
	1.1.4  访问元数据
	1.1.5  其它特性
1.2  ODBC
1.3  嵌入式SQL

#### 2  函数和过程

2.1  声明和调用
2.2  更强大的语法
2.3  外部语言过程

#### 3  触发器

3.1  触发器的语法
3.2  何时不用触发器

#### 4  递归查询

#### 5  高级聚集特性

5.1  排名
5.2  分窗

## 二  主要内容

​	SQL没有通用图灵机语言支持的强大特性，而且许多工作也无法仅仅依赖数据库完成。因此，需要使用某种程序设计语言与SQL交互，让应用程序可以访问数据库。主要方式是动态SQL和嵌入式SQL。
​	JDBC是Java语言支持的动态SQL。要用JDBC访问SQL数据库，首先要连接到数据库，然后可以调用`executeQuery()`方法和`executeUpdate()`方法执行SQL语句，查询结果用`ResultSet`对象处理。可以使用预备语句，它更加灵活，并且更加安全。JDBC还支持访问SQL数据库的元数据。ODBC是C/C++语言支持的动态SQL，其使用方法和JDBC类似。
​	嵌入式SQL在程序设计语言中嵌入SQL语句，并且使用预编译器对其预编译。使用游标执行查询过程，而非查询过程可以直接执行。各种程序设计语言都支持嵌入式SQL。

​	在SQL中可以定义和调用函数和过程。SQL提供了更强大的接近通用图灵机语言的语法支持函数和过程。也可以使用外部语言过程。

​	触发器被预先定义，并在满足某个条件时自动地执行。触发器可用于检查完整性约束，还可用于满足特定条件时自动地执行某项任务。触发器很有用，但如果有其它代替方法就不要使用触发器。

​	SQL支持递归查询，递归视图可以用它本身来定义。

​	SQL还支持其它高级聚集特性，如排名和分窗。排名可以在排序的元组集合中找出某元组的排序，而分窗用于对一定范围内的元组计算聚集函数。

## 三  重点梳理

- 理解并掌握动态SQL，理解并掌握JDBC和ODBC。
- 理解并掌握如何在SQL中使用函数和过程。
- 理解并掌握如何在函数中使用触发器。
- 了解SQL的递归查询。

## 四  难点解析

#### 1  什么是动态SQL？什么是嵌入式SQL？比较它们的区别。

#### 2  如何在JDBC中使用预备语句？使用预备语句有什么好处？

#### 3  在何种情况下使用触发器？

#### 4  如何使用SQL的递归查询？

## 五  重要图表

- P91  JDBC示例
  ![JDBC示例](D:\Learn\Note\Programming\数据库基础\Image\4 高级SQL\JDBC示例.png)
- P93  JDBC的预备语句
  ![JDBC的预备语句](D:\Learn\Note\Programming\数据库基础\Image\4 高级SQL\JDBC的预备语句.png)
- P96  ODBC示例
  ![ODBC示例](D:\Learn\Note\Programming\数据库基础\Image\4 高级SQL\ODBC示例.png)
- P102  函数和过程示例
  ![函数示例_1](D:\Learn\Note\Programming\数据库基础\Image\4 高级SQL\函数示例_1.png)
  ![函数示例_2](D:\Learn\Note\Programming\数据库基础\Image\4 高级SQL\函数示例_2.png)
  ![过程示例](D:\Learn\Note\Programming\数据库基础\Image\4 高级SQL\过程示例.png)
- P104 & P105  触发器示例
  ![触发器示例_1](D:\Learn\Note\Programming\数据库基础\Image\4 高级SQL\触发器示例_1.png)
  ![触发器示例_2](D:\Learn\Note\Programming\数据库基础\Image\4 高级SQL\触发器示例_2.png)
- P110  递归查询示例
  ![递归查询示例](D:\Learn\Note\Programming\数据库基础\Image\4 高级SQL\递归查询示例.png)

## 六  薄弱点清单



------

