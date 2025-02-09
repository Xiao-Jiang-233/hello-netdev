---
comments: true
---
# 应用 ACL

???+ note "注意"
    目前只考：简化流策略。也就是：基于接口，对转发的报文进行过滤，从而使设备能够进一步对过滤出的报文进行丢弃等处理。

## 配置命令

**traffic-filter** { **inbound** | **outbound** } **acl** *acl-number* : 在接口上配置基于ACL对报文进行过滤。

| 参数         | 参数说明                         | 取值                                                                             |
| ------------ | -------------------------------- | -------------------------------------------------------------------------------- |
| **inbound**  | 指定在接口入方向上配置报文过滤。 |                                                                                  |
| **outbound** | 指定在接口出方向上配置报文过滤。 |                                                                                  |
| **acl**      | 指定基于IPv4 ACL对报文进行过滤。 |                                                                                  |
| *acl-number* | 指定ACL的编号。                  | 整数形式。其中：<li>2000～2999表示基本ACL。</li><li>3000～3999表示高级ACL。</li> |

## 注意事项

- 过滤报文的匹配ACL规则：
    - 若报文匹配的规则的动作为deny，则直接丢掉该报文。
    - 若报文匹配的规则的动作为permit，则允许该报文通过。
    - 若报文没有匹配任何一条规则，则允许该报文通过。
- **traffic-filter** 命令所引用的ACL可以是未配置过的ACL（数字型ACL），用户可以在执行此命令后对引用的ACL进行配置。
- 一个接口的同一个方向上只能配置基于一个ACL进行报文过滤，如果需要更改 **traffic-filter** 命令所引用的ACL，则需要先执行 **undo** **traffic-filter** 命令取消基于原ACL的报文过滤。


## 使用实例

```text
Huawei> system-view
[Huawei] acl 3000
[Huawei-acl-adv-3000] rule 5 permit ip source 192.168.0.2 0
[Huawei-acl-adv-3000] quit
[Huawei] interface ethernet 2/0/0
[Huawei-Ethernet2/0/0] traffic-filter inbound acl 3000
```
