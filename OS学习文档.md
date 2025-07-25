## 1、页表相关

### 1.1 Clock algorithm——LRU实现算法

​	`Clock algorithm`（时钟算法）是一种 **近似实现 LRU（Least Recently Used）算法** 的页面置换算法，常用于 **操作系统的页面替换策略**。

### 🔁 算法步骤：

1. 指针指向一个页面。
2. 如果该页面的访问位为 **0**，就把它替换掉（选择它淘汰）。
3. 如果该页面访问位为 **1**，则：
   - 把访问位清零（`0`），
   - 指针向前走一步，检查下一个页面。
4. 重复这个过程，直到找到一个访问位为 0 的页面进行替换。