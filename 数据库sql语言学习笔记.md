#  数据库sql语言学习笔记



>“我们信赖上帝,除了上帝,任何人都必须用数据说话。”——爱德华•戴明

**增删改查是一个数据操作工具最基本的命令，在SQL中，这四种语句主要由以下关键字语句执行——**

- 增   insert
- 删   delete
- 改   update
- 查   select

## 1.Insert into 语句

功能：插入一行或多行语句

基本语法：

```python 
INSERT INTO TABLE_NAME (column1, column2, column3,...columnN)
VALUES (value1, value2, value3,...valueN);
```


## 2.Delete 语句

功能：用于删除行

基本语法：
```python
DELETE FROM table_name
WHERE some_column=some_value;
```


## 3.Update 语句

功能：更新表中已存在数据

基本语法：
```python
UPDATE table_name
SET column1=value1,column2=value2,...
WHERE some_column=some_value;
```


## 4.Select 语句



### 4.1 Select 基本语句

基本语法（可用*代表所有列）：
```python
SELECT column_name,column_name
FROM table_name;
```


### 4.2 Select ... where 语句

基本语法：
```python
SELECT column_name,column_name
FROM table_name
#指定条件
WHERE column_name operator value;
```


### 4.3 Select … order by 语句

功能：从数据库选取数据，进行升序（ASC 默认）或降序（DESC）排列

基本语法：
```python
SELECT column-list
FROM table_name
[WHERE condition]
[ORDER BY column1, column2, .. columnN] [ASC | DESC];
```


### 4.4 Select … group by 语句

功能：从数据库中选取数据，对相应数据进行分组

基本语法：
```python
SELECT column-list
FROM table_name
WHERE [ conditions ]
GROUP BY column1, column2....columnN
ORDER BY column1, column2....columnN
```


### 4.5 Select … join 语句

几种类型：
- INNER JOIN：如果表中有至少一个匹配，则返回行；
- LEFT JOIN：即使右表中没有匹配，也从左表返回所有的行；
- RIGHT JOIN：即使左表中没有匹配，也从右表返回所有的行；
- FULL JOIN：只要其中一个表中存在匹配，则返回行。

### 4.6 Select和其他语句共同使用（子查询）

子查询可以与 SELECT、INSERT、UPDATE 和 DELETE 语句一起使用，并可使用运算符如 =、<、>、>=、<=、IN、BETWEEN 等。
几个规则：
- 子查询必须用括号括起来。
-子查询在 SELECT 子句中只能有一个列，除非在主查询中有多列，与子查询的所选列进行比较。
-ORDER BY 不能用在子查询中，虽然主查询可以使用 ORDER BY。可以在子查询中使用 GROUP BY，功能与 ORDER BY 相同。
-子查询返回多于一行，只能与多值运算符一起使用，如 IN 运算符。
-BETWEEN 运算符不能与子查询一起使用，但是，BETWEEN 可在子查询内使用。

基本语法：
```python
--SELECT 语句中的子查询使用
SELECT column_name [, column_name ]
FROM   table1 [, table2 ]
WHERE  column_name OPERATOR
      (SELECT column_name [, column_name ]
      FROM table1 [, table2 ]
      [WHERE])
      
--INSERT 语句中的子查询使用
--INSERT 语句使用子查询返回的数据插入到另一个表中。
INSERT INTO table_name [ (column1 [, column2 ]) ]
   SELECT [ *|column1 [, column2 ] ]
   FROM table1 [, table2 ]
   [ WHERE VALUE OPERATOR ]

--UPDATE 语句中的子查询使用
--当通过 UPDATE 语句使用子查询时，表中单个或多个列被更新。
UPDATE table
SET column_name = new_value
[ WHERE OPERATOR [ VALUE ]
   (SELECT COLUMN_NAME
   FROM TABLE_NAME)
   [ WHERE) ]

--DELETE 语句中的子查询使用
DELETE FROM TABLE_NAME
[ WHERE OPERATOR [ VALUE ]
   (SELECT COLUMN_NAME
   FROM TABLE_NAME)
   [ WHERE) ]
```