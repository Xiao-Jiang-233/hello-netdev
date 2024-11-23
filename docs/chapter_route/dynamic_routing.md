# 动态路由 （Dynamic routing）

!!! note
    动态路由是宣告直连网段的

## RIP (Routing Information Protocol)

``` execline
[Huawei]rip
[Huawei-rip-1]version 2 # 必须为版本2
[Huawei-rip-1]network 192.168.10.0 # 必须是主类网络地址
```

## OSPF (Open Shortest Path First)

![OSPF多区域](dynamic_routing.assets/ospf_multi_area.png)

``` execline title="AR1:" hl_lines="5-8"
[AR1]ospf router-id ? # !!! 别瞎##配id
  IP_ADDR<X.X.X.X>  OSPF Private router ID value
  auto-recover      Automatic modification of conflicted router IDs
[AR1]ospf
[AR1-ospf-1]area 0
[AR1-ospf-1-area-0.0.0.0]network 192.168.10.0 0.0.0.3 # 这里是反掩码
[AR1-ospf-1-area-0.0.0.0]area 1
[AR1-ospf-1-area-0.0.0.1]network 192.168.5.0 0.0.0.3
```

``` execline title="AR3:" hl_lines="3-5"
[AR3]ospf
[AR3-ospf-1]area 1
[AR3-ospf-1-area-0.0.0.1]network 192.168.5.0 0.0.0.3
[AR3-ospf-1-area-0.0.0.1]network 192.168.1.0 0.0.0.255
[AR3-ospf-1-area-0.0.0.1]network 192.168.2.0 0.0.0.255
```

``` execline title="AR2:" hl_lines="4-8"
[AR2]ospf
[AR2-ospf-1]area 0
[AR2-ospf-1-area-0.0.0.0]network 192.168.10.0 0.0.0.3
[AR2-ospf-1-area-0.0.0.0]area 2
[AR2-ospf-1-area-0.0.0.1]network 192.168.6.0 0.0.0.3
```

省略其他
