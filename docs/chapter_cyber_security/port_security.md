# <center>端口安全（Port Security）</center>

## 配置端口安全动态MAC地址

```  execline
[Huawei]int g 0/0/1
[Huawei-GigabitEthernet0/0/1]port-security enable
[Huawei-GigabitEthernet0/0/1]port-security max-mac-num 5 # 默认为1，最大4096
[Huawei-GigabitEthernet0/0/1]port-security aging-time 300 # 单位是秒，默认不老化，最大1440
[Huawei-GigabitEthernet0/0/1]port-security protect-action ?
  protect   Discard packets                # 丢弃
  restrict  Discard packets and warning    # 丢弃 上报 （默认）
  shutdown  Shutdown                       # 关闭 上报
[Huawei-GigabitEthernet0/0/1]port-security protect-action shutdown
```

## 配置端口安全粘贴MAC地址

```  execline
[Huawei]int g 0/0/1
[Huawei-GigabitEthernet0/0/1]port-security enable
[Huawei-GigabitEthernet0/0/1]port-security mac-address sticky # 开启粘贴MAC地址
[Huawei-GigabitEthernet0/0/1]port-security mac-address sticky 6666-cccc-fff vlan 1 
# MAC地址格式为XXX-XXX-XXX，别忘vlan
[Huawei-GigabitEthernet0/0/1]port-security protect-action protect
```
