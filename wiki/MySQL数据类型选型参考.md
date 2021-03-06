
以下均已编码格式 **UTF-8** 为准。

- **L** 某个给定值的字节长度
- **M** 列值的最大长度

| 类型  | 字节 | 取值范围 | 建议宽度  |
| ------------ | ------------ | -------- | -------- |
| TINYINT  | 1  | **-128** ~ **127** | 2 |
| SMALLINT  | 2  | **-32768** ~ **32767** | 3-4 |
| MEDIUMINT | 3 | **-8388608** ~ **8388607** | 5-6 |
| INT | 4 | **-2147683648** ~ **2147683647** | 7-9，ID字段等自增字段为默认长度10，并设置为`unsigned` |
| BIGINT | 8 | **-9223372036854775808** ~ **9223372036854775807** | 20，注意要设置为`unsigned` |
| FLOAT | 4 | - | - |
| DOUBLE | 8 | - | - |
| DECIMAL(M,D) | - | - | - |
| CHAR(M) | 3*m | **0** ~ **255** |  固定长度 |
| VARCHAR(M) | L+1或L+2 | **1** ~ **65535** | 建议宽度为小于255，设为实际存储字段的最大长度  |  
| TEXT | L+2 | **65535** | 长度大于255个字符的使用该方式存储  |
| MEDIUMTEXT | L+3 | **2^24-1** | - |
| LONGTEXT | L+4 | **2^32-1** | - |
| DATE | 3 | **Y-m-d** | - |
| TIME | 3 | **h:i:s** | - |
| DATETIME | 8 | **Y-m-d H:i:s** | - |
| TIMESTAMP | 4 | **Y-m-d H:i:s** | created_at/updated_at/deleted_at等类型的时间使用该类型 |
| YEAR | 1 | **Y** | 存储年份 |

> 在MySQL中，行的最大长度为 **65535** 个 **字节**，因此会影响到 **VARCHAR** 字段能容纳的最大字符数目，但是不会影响到**TEXT**系列类型，因为它们数据存储于表数据是分开的。
