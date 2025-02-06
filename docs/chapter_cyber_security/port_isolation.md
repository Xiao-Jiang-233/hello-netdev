---
comments: true
---
# <center>端口隔离（Port isolation）</center>

## 配置命令

**port-isolate** **enable** [ **group** *group-id* ] : 使能端口隔离功能。

| 参数           | 参数说明               | 取值                               |
| -------------- | ---------------------- | ---------------------------------- |
| group group-id | 指定加入的端口隔离组。 | 整数形式，取值范围以实际设备为准。 |

**port-isolate** **mode** { **l2** | **all** } : 配置端口隔离模式。

| 参数    | 参数说明                             | 取值 |
| ------- | ------------------------------------ | ---- |
| **l2**  | 指定端口隔离模式为二层隔离三层互通。 |      |
| **all** | 指定端口隔离模式为二层三层都隔离。   |      |

## 注意事项

- 缺省情况下，端口隔离模式是二层隔离三层互通，若需要配置二三层都隔离可以执行 `port-isolate mode all` 命令配置。
- 同一端口隔离组的端口之间互相隔离，不同端口隔离组的端口之间不隔离。如果不指定 `group-id` 参数时，默认加入的端口隔离组为1
- 端口隔离模式配置为二层隔离三层互通后，如需配置二层三层都隔离的模式，请执行命令 `port-isolate mode all`。
- 端口隔离模式配置为二层三层都隔离后，如需配置二层隔离三层互通的模式，请执行命令 `port-isolate mode l2`。

## 使用实例

```text
[Huawei]int g 0/0/1
[Huawei-GigabitEthernet0/0/1]port link-type access
[Huawei-GigabitEthernet0/0/1]port default vlan 100
[Huawei-GigabitEthernet0/0/1]port-isolate enable group 1
[Huawei-GigabitEthernet0/0/1]port-isolate mode all
```
