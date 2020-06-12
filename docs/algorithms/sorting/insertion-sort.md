---
nav:
  title: 算法
  order: 2
group:
  title: 排序
  order: 2
title: 插入排序
order: 3
---

# 插入排序

**插入排序**（Insertion Sort）的代码实现虽然没有冒泡排序和选择排序那么简单粗暴，但它的原理应该是最容易理解的了，因为只要打过扑克牌的人都应该能够秒懂。插入排序是一种最简单直观的排序算法，它的工作原理是通过构建有序序列，对于未排序数据，在已排序序列中从后向前扫描，找到相应位置并插入。

插入排序和冒泡排序一样，也有一种优化算法，叫做拆半插入。

## 算法原理

插入排序的工作原理是通过构建有序序列，对于未排序数据，在已排序序列中从后向前扫描，找到相应位置并插入。插入排序在实现上，通常采用 in-place 排序（即只需用到 `O(1)` 的额外空间的排序），因而在从后向前扫描过程中，需要反复把已排序元素逐步向后挪位，为最新元素提供插入空间。

1. 从第一个元素开始，该元素可以认为已经被排序
2. 取出下一个元素，在已经排序的元素序列中从后向前扫描
3. 如果该元素（已排序）大于新元素，将该元素移到下一位置
4. 重复步骤 3，直到找到已排序的元素小于或者等于新元素的位置
5. 将新元素插入到该位置后
6. 重复步骤 2-5

```jsx | inline
import React from 'react';
import img from '../../assets/sorting/insertion-sort.gif';

export default () => <img alt="插入排序" src={img} width="64%" height="64%" />;
```

## 算法分析

- 平均时间复杂度：`O(n^2)`
- 最差时间复杂度：`O(n^2)`
- 空间复杂度：`O(1)`
- 排序方式：In-place
- 稳定性：稳定

如果插入排序的目标是把 n 个元素的序列升序排列，那么采用插入排序存在最好情况和最坏情况：

1. 最好情况：序列已经是升序排列，在这种该情况下，需要进行的比较操作需 `n - 1` 次即可
2. 最坏情况：序列是降序排列，那么此时需要进行的比较共有 `n * (n - 1) / 2` 次

插入排序的赋值操作是比较操作的次数减去 `n - 1` 次，平均来说插入排序算法复杂度为 `O(n^2)`

最优的空间复杂度为开始元素已排序，则空间复杂度为 0

最差的空间复杂度为开始元素为逆排序，则空间复杂度最坏时为 `O(n)`

平均的空间复杂度为 `O(1)`

## 算法实现

```js
const insertionSort = function(arr) {
  // 待排序序列正向遍历
  for (var i = 1; i < arr.length; i++) {
    // 当前需要排序的值
    const cur = arr[i];

    // 有序序列最后一个值的索引
    let j = i - 1;

    // 有序序列反向遍历
    while (j >= 0 && arr[j] > cur) {
      arr[j + 1] = arr[j];
      j--;
    }
    arr[j + 1] = cur;
  }
  return arr;
};
```