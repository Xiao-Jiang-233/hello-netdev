# 静态 NAT (Static Nat)

**nat** **static** **global** *global-address* **inside** *host-address* : 配置私网 IP 地址和公网 IP 地址的静态映射关系。

| 参数             | 参数说明                  | 取值             |
| ---------------- | ------------------------- | ---------------- |
| **global**       | 设置 NAT 的公网信息。     |                  |
| *global-address* | 指定 NAT 的公网 IP 地址。 | 点分十进制格式。 |
| **inside**       | 设置 NAT 的私网信息。     |                  |
| *host-address*   | 指定 NAT 的私网 IP 地址。 | 点分十进制格式。 |

## 使用实例

```text
[Huawei]int g0/0/2
[Huawei-GigabitEthernet0/0/2]nat static global 202.199.184.10 inside 192.168.100.1
```
