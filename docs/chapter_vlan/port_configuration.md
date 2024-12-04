---
comments: ture
---

# VLAN 端口配置

## 配置命令

__port__ __link-type__ { __access__ | __hybrid__ | __trunk__ } : 命令用来配置接口的链路类型。

| 参数       | 参数说明                      |
| ---------- | ----------------------------- |
| __access__ | 配置接口的链路类型为 Access。 |
| __hybrid__ | 配置接口的链路类型为 Hybrid。 |
| __trunk__  | 配置接口的链路类型为 Trunk。  |

__port__ __default__ __vlan__ _vlan-id_ : 命令用来配置接口的缺省 VLAN 并同时加入这个 VLAN。

| 参数      | 参数说明               | 取值                             |
| --------- | ---------------------- | -------------------------------- |
| _vlan-id_ | 配置缺省 VLAN 的编号。 | 整数形式，取值范围是 1 ～ 4094。 |

__port__ __trunk__ __allow-pass__ __vlan__ { { _vlan-id1_ [ __to__ vlan-id2 ] }&<1-10> | __all__} : 命令用来配置 Trunk 类型接口加入的 VLAN。

| 参数                           | 参数说明                                                                                                                                                                                                | 取值                                                                                           |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| _vlan-id1_ [ __to__ vlan-id2 ] | 指定 Trunk 类型接口加入的 VLAN，其中：<ul> <li> _vlan-id1_ 表示第一个 VLAN 的编号。</li> <li> __to__ _vlan-id2_ 表示最后一个 VLAN 的编号。 _vlan-id2_ 的取值必须大于等于 _vlan-id1_ 的取值。</li> </ul> | _vlan-id1_ 为整数形式，取值范围是 1 ～ 4094。<br>_vlan-id2_ 为整数形式，取值范围是 1 ～ 4094。 |
| __all__                        | 指定 Trunk 接口加入所有 VLAN。                                                                                                                                                                          |                                                                                                |

## 使用实例

### 配置接入端口 (Access port)

```text
[Huawei]interface GigabitEthernet 0/0/1
[Huawei-GigabitEthernet0/0/1]port link-type access
[Huawei-GigabitEthernet0/0/1]port default vlan 100
[Huawei-GigabitEthernet0/0/1]
```

### 配置干道端口 (Trunk port)

__情况 1:__ allow all

```text
[Huawei]interface GigabitEthernet 0/0/24
[Huawei-GigabitEthernet0/0/24]port link-type trunk
[Huawei-GigabitEthernet0/0/24]port trunk allow-pass vlan all
```

__情况 2:__ allow 部分 Vlan

```text
[Huawei]interface GigabitEthernet 0/0/24
[Huawei-GigabitEthernet0/0/24]port link-type trunk
[Huawei-GigabitEthernet0/0/24]port trunk allow-pass vlan 100 to 200
[Huawei-GigabitEthernet0/0/24]port trunk allow-pass vlan 300 350
[Huawei-GigabitEthernet0/0/24]dis this
#
interface GigabitEthernet0/0/24
 port link-type trunk
 port trunk allow-pass vlan 100 to 200 300 350
#
return
```

## 其他操作

### 批量配置

[port-group 使用方法](/chapter_vlan/port_group)

```text
[Huawei]port-group group-member g0/0/5 to g0/0/10
[Huawei-port-group]port link-type access
# 设备将自动配置:
[Huawei-GigabitEthernet0/0/5]port link-type access
[Huawei-GigabitEthernet0/0/6]port link-type access
[Huawei-GigabitEthernet0/0/7]port link-type access
[Huawei-GigabitEthernet0/0/8]port link-type access
[Huawei-GigabitEthernet0/0/9]port link-type access
[Huawei-GigabitEthernet0/0/10]port link-type access
```

### 接入端口改为干道端口

```text
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

```text
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
