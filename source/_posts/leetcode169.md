---
title: 数组中出现次数超过一半的数字
date: 2021-03-23 17:53:09
tags: leetcode
---

[leetcode链接](https://leetcode-cn.com/problems/shu-zu-zhong-chu-xian-ci-shu-chao-guo-yi-ban-de-shu-zi-lcof/)

## 描述

数组中有一个数字出现的次数超过数组长度的一半，请找出这个数字。
你可以假设数组是非空的，并且给定的数组总是存在多数元素

### 示例 1：

```bash
  输入: [1, 2, 3, 2, 2, 2, 5, 4, 2]
  输出: 2

 ```
 $$\mathrm{e}^{\pi\mathrm{i}} = -1$$
### 限制：

``` bash
1 <= 数组长度 <= 50000
```

### 解题思路：(C++)
#### 1、用map词典记录数字的数量，当某数字数量超过一半时，则找到目标数字，时间和空间复杂度为O(N)。
{% codeblock lang:Cpp %}
  int majorityElement(vector<int>& nums) {
    int num = nums[0];
    int size = nums.size();
    map<int, int> times;
    for (int i = 0; i < size; i++ ){
        num = nums[i];
        times[num] += 1;
        if(times[num] > size/2){
            return num;
        }
    }
    return num;
  }
{% endcodeblock %}
#### 2、对数组排序，因为出现数量大于数组的一半，所以排序后的数组中间位置的数则为目标数字
{% codeblock lang:Cpp %}
  int majorityElement(vector<int>& nums) {
    sort(nums.begin(), nums.end());
    return nums[nums.size()/2];
  }
{% endcodeblock %}
#### 3、摩尔投票法
  * 记目标数字的票数为+1，非目标数字票数为-1，因目标数字出现数量大于数组一半，所以无论数组如何排序，其票数和大于0。
  * 选定当前索引数字作为假定目标数字，此时和为1，索引增加，此时已有假定目标数字，不做更改，判断新的数字和假定目标数字是否相同，相同则和+1，否则-1，若和为0，则清除假定目标数字。
    此时分两种情况：
      <1> 两个数字中有1个目标数字
        此时两个数字计数和为0，对最终和无影响
      <2> 两个数字中有0个目标数字
        此时两个数字计数和也为0，因为非目标数字未与目标数字计数相消，所以消除后目标数字比例增加，最终和增大，但是对求取目标数字无影响
{% codeblock lang:Cpp %}
  int majorityElement(vector<int>& nums) {
    int target = nums[0];
    int vote = 1;
    for (int i = 1; i < nums.size(); i++){
        if(vote == 0){
            target = nums[i];
        }
        int num = nums[i];
        target == num ? vote++ : vote--;
    }
    return target;
  }
{% endcodeblock %}


