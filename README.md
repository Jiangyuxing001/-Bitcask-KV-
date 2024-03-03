# -Bitcask-KV-
该项目是一个基于 Bitcask 存储模型的 KV 数据库。Bitcask 是一种高性能的持久化存储引擎，其基本原理是采用了预写日志的数据存储方式，每一条数据在写入时首先会追加写入到数据文件中，然后更新内存索引，内存索引存储了 Key 和 Value 在磁盘上的位置，读取数据时，会先从内存中根据 key 找到对应 Value 的位置，然后再从磁盘中取出实际的 Value。基于这种模型，其读写性能都非常高效快速，因为每次写入实际上都是一次顺序 I/O 操作，然后更新内存，每次读取也是直接从内存中找到对应数据在磁盘上的位置。
