---
comments: true
---
# <center>端口安全（Port Security）</center>

## 配置命令

**port-security** **enable** : 使能端口安全功能。

**port-security** **aging-time** *time* : 配置端口安全动态MAC地址的老化时间。

| 参数   | 参数说明                    | 取值                                      |
| ------ | --------------------------- | ----------------------------------------- |
| *time* | 安全动态MAC地址的老化时间。 | 整数形式，取值范围是1～1440。单位为分钟。 |

**port-security** **max-mac-num** *max-number* : 配置端口安全MAC地址学习限制数。

| 参数         | 参数说明                    | 取值                |
| ------------ | --------------------------- | ------------------- |
| *max-number* | 端口安全MAC地址学习限制数。 | 取值范围是1～4096。 |

**port-security** **protect-action** { **protect** | **restrict** | **shutdown** } : 配置端口安全功能中当接口学习到的MAC地址数达到限制后的保护动作。

| 参数         | 参数说明                                                                               | 取值 |
| ------------ | -------------------------------------------------------------------------------------- | ---- |
| **protect**  | 当学习到的MAC地址数达到接口限制数时，接口将丢弃源地址在MAC表以外的报文。               |      |
| **restrict** | 当学习到的MAC地址数达到接口限制数时，接口将丢弃源地址在MAC表以外的报文，同时发出告警。 |      |
| **shutdown** | 当学习到的MAC地址数达到接口限制数时，接口将执行 error down 操作，同时发出告警。        |      |

**port-security** **mac-address** **sticky** : 使能接口Sticky MAC功能。

**port-security** **mac-address** **sticky** [ *mac-address* **vlan** *vlan-id* ] : 手动配置接口Sticky MAC表项。

| 参数         | 参数说明                    | 取值                                     |
| ------------ | --------------------------- | ---------------------------------------- |
| mac-address  | 配置为Sticky MAC的MAC地址。 | 格式为H-H-H，其中H为1至4位的十六进制数。 |
| vlan vlan-id | 配置VLAN的编号。            | 整数形式，取值范围是1～4094。            |

???+ note "注意"

    - 使能Sticky MAC功能后接口会将学习到的安全动态MAC地址转化为Sticky MAC。
    - 如果当前的Sticky MAC数还没有达到接口限制数，对于新学到的动态MAC地址继续转化为Sticky MAC，如果已经达到限制数，将丢弃该接口学习到的非Sticky MAC表项中的MAC地址，并根据接口保护模式的配置，决定是否上送trap告警。

## 注意事项

- 使能端口安全功能后，才可以配置端口安全保护动作、安全动态MAC学习限制数量、 Sticky MAC 功能。
- 当端口安全动态MAC的老化时间小于全局的MAC老化时间时，需要等到全局老化时间到达后才能老化该接口的安全动态MAC地址。
- 在没有使能 Sticky MAC 的情况下，该接口限制数用于限制接口学习的安全动态MAC地址数和手动配置的安全静态MAC数。
- 在使能 Sticky MAC 的情况下，该接口限制数用于限制接口学习的 Sticky MAC 数及手动配置的 Sticky MAC 数和安全静态MAC数。
- 缺省情况下，端口安全功能的保护动作为 **restrict** 。
- 当设备的接口设置对应的保护动作参数为 **shutdown** 时，接口学习到的MAC地址数超过限制数时，接口会自动执行 error down 操作，并且不会自动恢复。

## 使用实例

### 配置端口安全动态 MAC 地址

```text
[Huawei]int g 0/0/1
[Huawei-GigabitEthernet0/0/1]port-security enable
[Huawei-GigabitEthernet0/0/1]port-security max-mac-num 5 # 默认为1，最大4096
[Huawei-GigabitEthernet0/0/1]port-security aging-time 300 # 单位是分钟，默认不老化，最大1440
[Huawei-GigabitEthernet0/0/1]port-security protect-action shutdown
```

### 配置端口安全粘贴 MAC 地址

```text
[Huawei]int g 0/0/1
[Huawei-GigabitEthernet0/0/1]port-security enable
[Huawei-GigabitEthernet0/0/1]port-security mac-address sticky
[Huawei-GigabitEthernet0/0/1]port-security mac-address sticky 6666-cccc-fff vlan 1
[Huawei-GigabitEthernet0/0/1]port-security protect-action protect
```
