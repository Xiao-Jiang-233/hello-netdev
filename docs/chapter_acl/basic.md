# 基本ACL

``` execline
[Huawei]acl 2000 # 基本acl的范围为2000-2999
[Huawei-acl-basic-2000]rule deny source 192.168.1.0 0.0.0.255 # 拒绝1.0网段通过
[Huawei-acl-basic-2000]rule permit source 192.168.2.1 0 # 允许2.1主机通过
[Huawei-acl-basic-2000]int g 0/0/1
[Huawei-GigabitEthernet0/0/1]traffic-filter acl 2000
```

!!! tip
    基本ACL应在靠近目的端口上配置
