

## SQL基础

### SQL语言分类

DML

- 添加
- 修改
- 删除 
- 查询

DCL

- 用户
- 事务
- 权限

DDL

- 逻辑库 
- 数据表
- 视图
- 索引



### SQL语句注意事项

- SQL语句不区分大小写，但是字符串区分大小写
  SELECT "Hellowor1d";
- SQL语句必须以分号结尾
- SQL语句中的空白和换行没有限制，但是不能破坏语法

### SQL语句的注释
- SQL语句的注释有两种，分别如下：

```sql
 ＃这是一段注释文字
/* 这是另一段注释文字*/
```



### 创建逻辑库
```sql
CREATE DATABASE 逻辑库名称； # 创建逻辑库
SHOW DATABASES; # 展示所有的逻辑库
DROP DATABSE 逻辑库名称; # 删除逻辑库
```

### 创建数据表
```sql
CREATE TABLE 数据表（
  列名1 数据类型 [约束] [COMMENT 注释]，
  列名2 数据类型 [约束] [COMMENT 注释]
）[COMMENT =注释]；

CREATE TABLE student (
  id INJ UNSIGNED PRIMARY KEY,
  name VARCHAR(20) NOT NULL,
  sex CHAR(1) NOT NULL,
  birthday DATE NOT NULL,
  tel CHAR(11) NOT NULL,
  remark VARCHAR(200)
 )
 CREATE TABLE `t_student`(
   `id` INT NOT NULL COMMENT '学生id',
   `name` VARCHAR(20) NOT NULL COMMENT '学生姓名',
   `sex` ENUM('男','女') NOT NULL DEFAULT '男' COMMENT '学生性别',
   PRIMARY KEY (`id`)
 ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

### 数据表的其他操作
```sql
SHOW tables; #展示逻辑库的数据表
DESC student; #展示对应表的详细信息(定义)
SHOW CREATE TABLE student; #显示创建表的语句
DROP TABLE student; # 删除数据表
```



## 数据类型

### 数字

| 类型      | 大小   | 说明          |
| --------- | ------ | ------------- |
| TINYINT   | 1字节  | 小整数        |
| SMALLINT  | 2字节  | 普通整数      |
| MEDIUMINT | 3字节  | 普通整数      |
| INT       | 4字节  | 较大整数      |
| BIGINT    | 8字节  | 大整数        |
| FLOAT     | 4字节  | 单精度浮点数  |
| DOUBLE    | 8字节  | 双精度浮点数  |
| DECIMAL   | ------ | DECIMAL(10.2) |



### 字符串

| 类型       | 大小           | 说明             |
| ---------- | -------------- | ---------------- |
| CHAR       | 1-255字符      | 固定长度字符串   |
| VARCHAR    | 1-65535字符    | 不固定长度字符串 |
| TEXT       | 1-65535字符    | 不确定长度字符串 |
| MEDIUMTEXT | 1-1千6百万字符 | 不确定长度字符串 |
| LONGTEXT   | 1-42亿字符     | 不确定长度字符串 |

### 日期类型

| 类型      | 大小  | 说明     |
| --------- | ----- | -------- |
| DATE      | 3字节 | 日期     |
| TIME      | 3字节 | 时间     |
| YEAR      | 1字节 | 年份     |
| DATETIME  | 8字节 | 日期时间 |
| TIMESTAMP | 4字节 | 时间戳   |



## 修改表结构

### 添加字段

```sql
ALTER TABLE 表名称
ADD 列1 数据类型 [约束] [COMMENT 注释],
ADD 列2 数据类型 [约束] [COMMENT 注释],
#....

ALTER TABLE student
ADD address VARCHAR (200) NOT NULL,
ADD home_tel CHAR (11) NOT NULL;
```

### 修改字段类型和约束

```sql
ALTER TABLE 表名称
MODIFY 列1 数据类型 [约束] [COMMENT 注释],
MODIFY 列2 数据类型 [约束] [COMMENT 注释],
#....

ALTER TABLE student
MODIFY home tel VARCHAR (20) NOT NULL;
```

### 修改字段名称
```sql
ALTER TABLE 表名称
CHANGE 列1 新列名1 数据类型 [约束] [COMMENT 注释],
CHANGE 列2 新列名2 数据类型 [约束] [COMMENT 注释],
#....

ALTER TABLE student
CHANGE address home address VARCHAR (200) NOT NULL;
```

### 删除字段
```sql
ALTER TABLE 表名称
DROP 列1，
DROP 列2，
#....

ALTER TABLE student
DROP home_address,
DROP home_tel;
```




