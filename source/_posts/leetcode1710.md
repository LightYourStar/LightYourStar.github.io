---
title: 卡车上的最大单元数
date: 2021-03-26 11:18:02
tags: leetcode
---

[leetcode链接](https://leetcode-cn.com/problems/maximum-units-on-a-truck/submissions/)

## 描述
请你将一些箱子装在 一辆卡车 上。给你一个二维数组 boxTypes ，其中 boxTypes[i] = [numberOfBoxesi, numberOfUnitsPerBoxi] ：

    · numberOfBoxesi 是类型 i 的箱子的数量。
    · numberOfUnitsPerBoxi 是类型 i 每个箱子可以装载的单元数量。
整数 truckSize 表示卡车上可以装载 箱子 的 最大数量 。只要箱子数量不超过 truckSize ，你就可以选择任意箱子装到卡车上。

返回卡车可以装载 单元 的 最大 总数。

### 示例 1：
```bash
    输入：boxTypes = [[1,3],[2,2],[3,1]], truckSize = 4
    输出：8
    解释：箱子的情况如下：
    - 1 个第一类的箱子，里面含 3 个单元。
    - 2 个第二类的箱子，每个里面含 2 个单元。
    - 3 个第三类的箱子，每个里面含 1 个单元。
    可以选择第一类和第二类的所有箱子，以及第三类的一个箱子。
    单元总数 = (1 * 3) + (2 * 2) + (1 * 1) = 8

```
### 示例 2：
```bash
    输入：boxTypes = [[5,10],[2,5],[4,7],[3,9]], truckSize = 10
    输出：91

```
### 提示：
· 1 <= boxTypes.length <= 1000
· 1 <= numberOfBoxesi, numberOfUnitsPerBoxi <= 1000
· 1 <= truckSize <= 106

### 解题思路：(C++)
#### 贪心算法
* 每次将能装载最大单元数量的箱子放到卡车上
* 寻找当前剩余能装载最大单元数量的箱子，可以通过排序让箱子按照装载的单元数量从大到小排序

{% codeblock lang:Cpp %}
    int maximumUnits(vector<vector<int>>& boxTypes, int truckSize) {
        sort(boxTypes.begin(), boxTypes.end(), [](const auto& a, const auto& b){return a[1] > b[1];});
        //使用lambda表达式结合sort进行排序

        int res = 0;
        int n = 0;
        for(int i = 0; i< boxTypes.size() && truckSize > 0; i++){
            n = min(truckSize, boxTypes[i][0]);
            truckSize -= n;
            res += n * boxTypes[i][1];
        }
        return res;
    }
{% endcodeblock %}

