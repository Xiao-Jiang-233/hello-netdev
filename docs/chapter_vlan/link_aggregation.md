# <center>链路聚合 (Link Aggregation)</center>

## 创建Eth-Trunk接口

``` execline
[LSW1]interface Eth-Trunk 1
[LSW1-Eth-Trunk1]port link-type trunk
[LSW1]int g0/0/1
[LSW1-GigabitEthernet0/0/1]eth-trunk 1
```
