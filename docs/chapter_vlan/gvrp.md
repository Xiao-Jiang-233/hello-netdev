# <center>GVRP (Generic Attribute Registration Protocol)</center>

没啥要写的，拢共两句话。

## 配置命令

**gvrp** : 用来使能全局GVRP功能，或者使能接口GVRP功能。

**gvrp** **registration** { **fixed** | **forbidden** | **normal** } : 用来设置GVRP接口注册模式。

| 参数          | 参数说明                | 取值 |
| ------------- | ----------------------- | ---- |
| **fixed**     | 指定Fixed注册模式。     |      |
| **forbidden** | 指定Forbidden注册模式。 |      |
| **normal**    | 指定Normal注册模式。    |      |

## 使用实例

```text
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
