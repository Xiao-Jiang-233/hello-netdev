# STP基础操作

## 协议配置

修改模式:

``` execline title=""
[Huawei]stp mode ?
  mstp  Multiple Spanning Tree Protocol (MSTP) mode
  rstp  Rapid Spanning Tree Protocol (RSTP) mode
  stp   Spanning Tree Protocol (STP) mod
```

修改优先级:

=== "方法一"
    ``` execline title=""
    [Huawei]stp priority 0 # (1)!
    ```

    1. 网桥优先级取值范围：`0~65535`，缺省值：`32768`，步长为`4096`，一般根桥设为 **0**，备份根桥设为 **4096**

=== "方法二"
    ``` execline title=""
    [Huawei]stp root ?
      primary    Primary root switch      # 根桥
      secondary  Secondary root switch    # 备份根桥
    ```

端口开销配置:

``` execline
[LSW1]int g0/0/1
[LSW1-GigabitEthernet0/0/1]stp cost 100
```
