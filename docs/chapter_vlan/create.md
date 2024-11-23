# 创建Vlan

## 创建单个vlan

=== "方法一"
    ``` execline
    [Huawei]vlan 100
    [Huawei-vlan100] # 这会进入Vlan视图
    ```

=== "方法二"
    ``` execline
    [Huawei]vlan batch 100
    ```

## 批量创建Vlan

=== "方法一"
    ``` execline
    [Huawei]vlan batch 100 to 200   # 这会创建vlan100到vlan200
    ```

=== "方法二"
    ``` execline
    [Huawei]vlan batch 100 200  # 这会创建vlan100和vlan200
    ```

## 删除Vlan

``` execline
[Huawei]undo vlan 100
```
