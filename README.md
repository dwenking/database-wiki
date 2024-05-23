# database-wiki

## MySQL

### 数据类型

* 字符型：LONGBLOB、LONGTEXT、MEDIUMBLOB、MEDIUMTEXT、BLOB、TEXT、TINYBLOB、TINYTEXT、VARCHAR、CHAR
* 整型：BIGINT、INT、MEDIUMINT、SMALLINT、TINYINT、BIT
* 浮点型：DOUBLE、FLOAT、DECIMAL
* 布尔型：BOOLEAN
* 日期型：TIMESTAMP、DATETIME、YEAR、DATE、TIME

## MariaDB

### 数据类型

* 字符型：LONGBLOB、LONGTEXT、MEDIUMBLOB、MEDIUMTEXT、BLOB、TEXT、TINYBLOB、TINYTEXT、VARCHAR、CHAR、BINARY、VARBINARY
* 整型：BIGINT、INT、MEDIUMINT、SMALLINT、TINYINT、BIT
* 浮点型：DOUBLE、FLOAT、DECIMAL
* 布尔型：BOOLEAN
* 日期型：TIMESTAMP、DATETIME、YEAR、DATE、TIME

## Postgres

### 数据类型

* 字符型：TEXT、VARCHAR、CHAR
* 整型：BIGINT、INT、SMALLINT、TINYINT、BIT、SMALLSERIAL、SERIAL、BIGSERIAL、MONEY
* 浮点型：DOUBLE、REAL、DECIMAL
* 布尔型：BOOLEAN
* 日期型：TIMESTAMP、YEAR、DATE、TIME

## DuckDB

DuckDB是一个In-Process OLAP，与传统OLAP系统相比，In-Process OLAP分析直接在事务数据库内进行，无需将数据迁移到另一个系统。

DuckDB的优势：

* 没有外部依赖，能够快速部署
* 不需要维护DBMS服务器软件，其本身不作为单独进程运行，而是嵌入到宿主进程中。这使得数据传输非常高效。
* 列状存储，能够向量化处理数据

### 数据类型

* 字符型：BLOB、VARCHAR
* 整型：
  * 有符号：HUGEINT、BIGINT、INT、SMALLINT、TINYINT
  * 无符号：UHUGEINT、UBIGINT、UINTEGER、USMALLINT、UTINYINT、BIT
* 浮点型：DOUBLE、FLOAT、DECIMAL
* 布尔型：BOOLEAN
* 日期型：TIMESTAMP、TIMESTAMPTZ、TIME
* 其他：UUID

## 技巧整理

### 类型转换

* 整数值转换为FLOAT时，会因为FLOAT存储精度有限导致的四舍五入而造成一些值的不一致
* 数值类型做比较时，如果需要转换，默认转换为双精度DOUBLE类型比较
* 使用BLOB类型时，应用内要记得转换编码

### 极端值整理

| Name                      | Min                                     | Max                                     |
| ------------------------- | --------------------------------------- | --------------------------------------- |
| TINYINT                   | -128                                    | 127                                     |
| SMALLINT                  | -32768                                  | 32767                                   |
| INTEGER                   | -2147483648                             | 2147483647                              |
| BIGINT                    | -922337203685477580                     | 9223372036854775807                     |
| HUGEINT                   | -17014118346046923173168730371588410572 | 170141183460469231731687303715884105727 |
| UTINYINT                  | 0                                       | 255                                     |
| USMALLINT                 | 0                                       | 65535                                   |
| UINTEGER                  | 0                                       | 4294967295                              |
| UBIGINT                   | 0                                       | 18446744073709551615                    |
| UHUGEINT                  | 0                                       | 340282366920938463463374607431768211455 |
| FLOAT/REAL（精度至少6位） | 1e-37                                   | 1e+37                                   |
| DOUBLE（精度至少15位）    | 1e-307                                  | 1e+308                                  |
| MONEY（精度两位小数）     | -92233720368547758.08                   | +92233720368547758.07                   |

### 一些有用工具

[https://dbfiddle.uk/](https://dbfiddle.uk/)
[https://www.db-fiddle.com/](https://www.db-fiddle.com/)
