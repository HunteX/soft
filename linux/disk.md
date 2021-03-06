<!-- toc -->
# 磁盘相关知识

机械磁盘，通常缩写为HDD，机械磁盘有磁道寻址的时间，随机读写是性能会变差。

固态磁盘，通常缩写为SSD，不需要寻道，随机读写和连续读写效率均较高。

磁盘接口主要有：IDE、SCSI、SAS、SATA、FC等。

在具体使用的时候，可以将磁盘作为独立磁盘用，在每个磁盘上划分逻辑分区，或者将多个独立磁盘组合成一个逻辑磁盘，譬如RAID，RAID分为RAID0、RAID1、RAID5、RAID10，或者将磁盘组合成一个存储集群，通过NFS、SMB、iSCSI等网络存储协议接入服务器。

磁盘被Linux认作是块设备，拥有主设备号和次设备号，主设备号用于区分设备类型，面向驱动程序，次设备号是同类设备的唯一编号。

## 磁盘数据最小读取单位

机械磁盘的最小读取单位是扇区，每个扇区一般为512字节。

固态磁盘的最小读取单位是页，通常是4KB、8KB。

## 磁盘数据最小管理单位

逻辑块是磁盘上连续的扇区或者页，逻辑块是磁盘数据的最小管理单位。

## 磁盘性能指标

**使用率**：磁盘处理I/O的时间占比，使用率过高超过80%，说明磁盘I/O存在性能瓶颈。

**饱和度**：磁盘处理I/O的繁忙程度，饱和度为100%时，磁盘已经无法接收新的I/O请求。

**IOPS**：每秒钟的I/O操作次数。

**吞吐量**：每秒的数据吞吐量。

**响应时间**：I/O请求发出与收到响应的间隔时间。

磁盘使用率高不等于磁盘饱和，如果每次I/O操作的数据量很少，磁盘的使用率高，但是饱和度不高，可以继续接收新的I/O请求。(感觉饱和度有点类似于带宽占比，是和吞吐量相关的)

## 磁盘性能测试工具

fio，测试时需要考虑不同I/O大小、随机读、顺序读、随机写、顺序写等。

## 参考
