---
title:  数组中出现次数超过一半的数字
---
## 描述

数组中有一个数字出现的次数超过数组长度的一半，请找出这个数字。
你可以假设数组是非空的，并且给定的数组总是存在多数元素

### 示例 1：

```bash
  输入: [1, 2, 3, 2, 2, 2, 5, 4, 2]
  输出: 2

 ```
### 限制：

``` bash
1 <= 数组长度 <= 50000
```

### 解题思路：(C++)
  #### 1、用map词典记录数字的数量，当某数字数量超过一半时，则找到该数字
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
  #### 2、对数组排序，因为出现数量大于数组的一半，所以排序后的数组中间位置的数则为该数字
{% codeblock lang:Cpp %}
  sort(nums.begin(), nums.end());
  return nums[nums.size()/2];
{% endcodeblock %}
[链接](https://leetcode-cn.com/problems/shu-zu-zhong-chu-xian-ci-shu-chao-guo-yi-ban-de-shu-zi-lcof/)

