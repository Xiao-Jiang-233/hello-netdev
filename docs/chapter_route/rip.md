---
comments: true
---
# RIP (Routing Information Protocol)

## 配置命令

**rip** : 使能指定的RIP进程。

**version** { **1** | **2** } : 指定一个全局RIP版本。

| 参数 | 参数说明      | 取值 |
| ---- | ------------- | ---- |
| 1    | 指定RIP-1版本 |      |
| 2    | 指定RIP-2版本 |      |

**network** *network-address* : 对指定网段接口使能RIP路由。

| 参数              | 参数说明                                            | 取值             |
| ----------------- | --------------------------------------------------- | ---------------- |
| *network-address* | 指定使能RIP的网络地址。该地址必须是自然网段的地址。 | 点分十进制形式。 |

## 使用实例

```text
<Huawei> system-view
[Huawei] rip
[Huawei-rip-1]version 2 # 指定为 RIP 版本2
[Huawei-rip-1]network 192.168.10.0
```
