---
title: hello,vue
date: 2021-03-18
categories:
 - python
---

# 已经安装的第三方库IDLE导入失败的问题解决

## 验证

点击IDLE上面的File-Path Browser，就会显示IDLE导入第三方库的默认路径

## 解决

sys.path.append()只能暂时增加路径，永久性增加的话需要在环境变量中增加PYTHONPATH这个变量，然后在变量值写入第三方库的路径，一般在Python文件夹下的Lib\site-packages