# <center>链路聚合 (Link Aggregation)</center>

## 配置命令

**eth-trunk** _trunk-id_ : 用来将当前接口加入到指定Eth-Trunk中。

| 参数       | 参数说明            | 取值                           |
| ---------- | ------------------- | ------------------------------ |
| _trunk-id_ | 指定Eth-Trunk的ID。 | 整数形式，具体以实际设备为准。 |

## 使用实例

```text
[LSW1]interface Eth-Trunk 1
[LSW1-Eth-Trunk1]port link-type trunk
[LSW1]int g0/0/1
[LSW1-GigabitEthernet0/0/1]eth-trunk 1
```

## 注意事项

- 两端设备Eth-Trunk中包含的成员接口数目应该相等，而且两端设备的接口之间由直连网线连接。
- 一个Eth-Trunk接口中的成员接口必须是以太网类型和速率相同的接口。以太网类型和速率不同的接口不能加入同一个Eth-Trunk接口，如GE接口和FE接口不能加入同一个Eth-Trunk接口。
