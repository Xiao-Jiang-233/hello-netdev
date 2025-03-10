---
comments: true
---
# 静态路由（Static routing）

## 配置命令

**ip** **route-static** *ip-address* { *mask* | *mask-length* } { *nexthop-address* | *interface-type* *interface-number* } : 配置静态路由。

| 参数                                | 参数说明                                                                              | 取值                         |
| ----------------------------------- | ------------------------------------------------------------------------------------- | ---------------------------- |
| *ip-address*                        | 指定目的IP地址。                                                                      | 点分十进制格式。             |
| *mask*                              | 指定IP地址的掩码。                                                                    | 点分十进制格式。             |
| *mask-length*                       | 指定掩码长度。因为32位的掩码要求“1”是连续的，点分十进制格式的掩码可以用掩码长度代替。 | 整数形式，取值范围是 0～32。 |
| *nexthop-address*                   | 指定路由的下一跳的IP地址。                                                            | 点分十进制格式。             |
| *interface-type* *interface-number* | 指定路由转发报文的接口类型和接口号。                                                  |                              |

**undo** **ip** **route-static** **all** : 删除所有IPv4单播静态路由。

## 注意事项

- 静态路由如果不配置优先级，默认优先级为60。
- 如果目的IP地址和掩码都为0.0.0.0，配置的路由为缺省路由。如果检查路由表时没有找到相关路由，则将使用缺省路由进行报文转发。
- 配置不同的优先级，可实现不同的路由管理策略。例如，为同一目的地配置多条路由，如果指定相同的优先级，则实现路由负载分担；如果指定不同的优先级，则实现路由备份。
- 配置静态路由时，可根据实际需要指定出接口或下一跳地址。对于点到点接口，只需指定出接口；对于广播类型接口，必须指定下一跳。
- 在某些情况下，如链路层被PPP封装，即使不知道对端地址，也可以在路由器配置时指定出接口。这样，即使对端地址发生了改变也无须改变该路由器的配置。
