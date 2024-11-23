# Vlan端口配置

## 配置接入端口 (Access port)

``` execline
[Huawei]interface GigabitEthernet 0/0/1
[Huawei-GigabitEthernet0/0/1]port link-type access 
[Huawei-GigabitEthernet0/0/1]port default vlan 100
[Huawei-GigabitEthernet0/0/1]
```

## 配置干道端口 (Trunk port)

**情况1:** allow all

``` execline  hl_lines="3"
[Huawei]interface GigabitEthernet 0/0/24
[Huawei-GigabitEthernet0/0/24]port link-type trunk
[Huawei-GigabitEthernet0/0/24]port trunk allow-pass vlan all
```

**情况2:** allow 部分Vlan

``` execline hl_lines="3 4"
[Huawei]interface GigabitEthernet 0/0/24
[Huawei-GigabitEthernet0/0/24]port link-type trunk
[Huawei-GigabitEthernet0/0/24]port trunk allow-pass vlan 100 to 200 # (1)!
[Huawei-GigabitEthernet0/0/24]port trunk allow-pass vlan 300 350
[Huawei-GigabitEthernet0/0/24]dis this
#
interface GigabitEthernet0/0/24
 port link-type trunk
 port trunk allow-pass vlan 100 to 200 300 350
#
return
```

1. `port trunk allow-pass vlan`后面可以跟三种参数：`all`、`单个vlan`、`范围(to)`

    其中1只能单独使用，2和3可以无限组合

    eg: `port trunk allow-pass vlan 60 to 65 70 to 80 100`

    但是不能: `port trunk allow-pass vlan 60 to 65 to 80` to必须成对使用

## 其他操作

### 批量配置

``` execline
[Huawei]port-group group-member g0/0/5 to g0/0/10 # (1)!
[Huawei-port-group]port link-type access
# 设备将自动配置:
[Huawei-GigabitEthernet0/0/5]port link-type access
[Huawei-GigabitEthernet0/0/6]port link-type access
[Huawei-GigabitEthernet0/0/7]port link-type access
[Huawei-GigabitEthernet0/0/8]port link-type access
[Huawei-GigabitEthernet0/0/9]port link-type access
[Huawei-GigabitEthernet0/0/10]port link-type access
```

1. `port-group group-member`后跟的参数情况和`port trunk allow-pass vlan`基本一致

    但是：一是只能写`端口类型`**+**`端口名字`，二是没有`all`

### 接入端口改为干道端口

``` execline
[Huawei-GigabitEthernet0/0/1]undo port default vlan
[Huawei-GigabitEthernet0/0/1]undo port link-type 
[Huawei-GigabitEthernet0/0/1]Port link-type trunk
[Huawei-GigabitEthernet0/0/1]dis this
#
interface GigabitEthernet0/0/1
 port link-type trunk
#
return
```

### 干道端口改为接入端口

``` execline
[Huawei-GigabitEthernet0/0/24]undo port trunk allow-pass vlan all
[Huawei-GigabitEthernet0/0/24]port trunk allow-pass vlan 1 # 注意！
[Huawei-GigabitEthernet0/0/24]undo port link-type 
[Huawei-GigabitEthernet0/0/24]port link-type access 
[Huawei-GigabitEthernet0/0/24]display this 
#
interface GigabitEthernet0/0/24
 port link-type access
#
return
```
