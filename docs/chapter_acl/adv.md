# 高级ACL

``` execline
[Huawei]acl 3000 # 高级ACL的范围为3000-3999
[Huawei-acl-adv-3000]rule permit ip source 192.168.1.0 0.0.0.255 destination 192.168.2.0 0.0.0.255
# 允许1.0网段访问2.0网段
[Huawei-acl-adv-3000]rule permit udp source 192.168.3.1 0 destination 192.168.4.1 0 destination-port eq 80
# 允许3.1主机访问4.1服务器上的web服务
[Huawei-acl-adv-3000]rule deny tcp source 192.168.2.0 0.0.0.255 destination 192.168.3.1 0 destination-port rang 20 21
# 拒绝2.0网段访问3.1服务器上的ftp服务
Huawei-acl-adv-3000]rule deny icmp source 192.168.3.1 0 destination 192.168.5.1 0
# 拒绝3.1主机ping通5.1主机
[Huawei-acl-adv-3000]int g 0/0/1
[Huawei-GigabitEthernet0/0/1]traffic-filter acl 3000
```

!!! tip
    1. 高级ACL应在靠近目的端口上配置
    2. 协议常用的有 `ip`, `tcp`, `icmp`, `udp`
    3. `destination-port`后的比较符有`rang`(范围), `eq`(等于), `gt`(大于), `lt`(等于)
