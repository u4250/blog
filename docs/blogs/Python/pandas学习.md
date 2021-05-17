---
title: pandas学习
date: 2021-05-17
categories:
 - python
tags:
 - pandas
---

## 一.pandas基础

### 1.基础函数

**特征统计函数**

对序列使用 `unique` 和 `nunique` 可以分别得到其唯一值组成的列表和唯一值的个数

`value_counts` 可以得到唯一值和其对应出现的频数：

```python
In [57]: df['School'].unique()
Out[57]:
array(['Shanghai Jiao Tong University', 'Peking University',
'Fudan University', 'Tsinghua University'], dtype=object)
In [58]: df['School'].nunique()
Out[58]: 4
```

**替换函数**

逻辑替换包括了 `where` 和 `mask` ，这两个函数是完全对称的：where 函数在传入条件为 <u>False</u> 的对应行进行 替换，而 mask 在传入条件为 <u>True</u> 的对应行进行替换，当不指定替换值时，替换为缺失值。

**排序函数**

排序共有两种方式，其一为值排序，其二为索引排序，对应的函数是 `sort_values` 和 `sort_index`。默认参数 <u>ascending=True</u> 为升序：

```python
#在排序中，进场遇到多列排序的问题，比如在体重相同的情况下，对身高进行排序，并且保持身高降序排列，体重升序排列：
df_demo.sort_values(['Weight','Height'],ascending=[True,False]).head()
#索引排序的用法和值排序完全一致，只不过元素的值在索引中，此时需要指定索引层的名字或者层号，用参数 level 表示。另外，需要注意的是字符串的排列顺序由字母顺序决定。
df_demo.sort_index(level=['Grade','Name'],ascending=[True,False]).head()

```

**apply方法**



