# 静态路由（Static routing）

!!! note
    静态路由是做非直连网段的

``` execline
[Huawei]ip route-static 192.168.100.0 255.255.255.0 192.168.10.2
#                       (目的子网号)    (目的子网掩码)  (下一条地址)
[Huawei]ip route-static 192.168.200.0 255.255.255.0 g0/0/0
#                       (目的子网号)    (目的子网掩码)  (出端口)
```

!!! tip ""
    1. 是目的<strong>子网掩码</strong>，而不是<i>反码</i> ！！！
    2. 在串行接口（serial）上，无法使用下一条地址，只能使用<strong>出端口</strong>
    3. 这是串行接口链路：RA------------------------------RB

## 默认路由（Default route）

!!! abstract ""
    默认路由是一种特殊的静态路由

``` execline
[Huawei]ip route-static 0.0.0.0 0.0.0.0 192.168.10.2
```
