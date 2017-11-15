### 显示表
**SHOW TABLES**;
### 如果没有我们想要的表，就创建一个
**CREATE TABLE** table_name (
	列名1 数据类型(数据长度),
	列名2 数据类型(数据长度),
	列名3 数据类型(数据长度),
	...
);

### 创建一个复杂的表　带有约束的表：
#### 约束主要有五种，可以写在后面，或单独写
***
#### 部门表
```
CREATE TABLE department
(
  dpt_name   CHAR(20) NOT NULL,*还可以添加多个约束*
  people_num INT(10) DEFAULT '10',
  CONSTRAINT dpt_pk PRIMARY KEY (dpt_name)　*约束　重命名　约束类型　(元组多列可以做一个主键)*
 );
```
#### 雇员表<---关联--->部门表
```
CREATE TABLE employee
(
  id      INT(10) PRIMARY KEY,
  name    CHAR(20),
  age     INT(10),
  salary  INT(10) NOT NULL,
  phone   INT(12) NOT NULL,
  in_dpt  CHAR(20) NOT NULL,
  UNIQUE  (phone),
  CONSTRAINT emp_fk FOREIGN KEY (in_dpt) REFERENCES department(dpt_name)　*in_dpt字段关联了 dapartment库的dpt_name字段，并且不能超出他的取值范围*
 );
```
#### 项目表<--- 关联---> 部门表
```
CREATE TABLE project
(
  proj_num   INT(10) NOT NULL,
  proj_name  CHAR(20) NOT NULL,
  start_date DATE NOT NULL,
  end_date   DATE DEFAULT '2015-04-01',
  of_dpt     CHAR(20) REFERENCES department(dpt_name),
  CONSTRAINT proj_pk PRIMARY KEY (proj_num,proj_name)
 );
```

