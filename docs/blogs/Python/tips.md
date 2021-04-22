---
title: hello,vue
date: 2021-04-22
tags:
 - 小技巧
categories:
 - python
---

## matplotlib

```python
# 对dataform做聚合分析画多组条形图
df.groupby('岗位名称')['信息水平'].value_counts().unstack().plot(kind = 'bar',width=0.8,rot=0)
```

