# <center>GVRP (Generic Attribute Registration Protocol)</center>

没啥要写的，拢共两句话。

``` execline
[Huawei]gvrp
[Huawei]vlan batch 10 20
[Huawei]int g0/0/1
[Huawei-GigabitEthernet0/0/1]port link-type trunk
[Huawei-GigabitEthernet0/0/1]port trunk allow-pass vlan all
[Huawei-GigabitEthernet0/0/1]gvrp registration ?
  fixed      Registration type fixed        # 固定
  forbidden  Registration type forbidden    # 禁止
  normal     Registration type normal       # 正常（默认）
```
