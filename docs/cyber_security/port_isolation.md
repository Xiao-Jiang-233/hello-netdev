# <center>端口隔离（Port isolation）</center>

``` execline
[Huawei]int g 0/0/1
[Huawei-GigabitEthernet0/0/1]port link-type access 
[Huawei-GigabitEthernet0/0/1]port default vlan 100
[Huawei-GigabitEthernet0/0/1]port-isolate enable group 1 #取值为1-64
```
