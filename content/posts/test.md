---
title: "画布"
date: 2023-10-07T13:57:51+08:00
draft: false
tags:
- matplotlib
thumbnailImagePosition: left
thumbnailImage: //d1u9biwaxjngwg.cloudfront.net/tag-plugins-showcase/car-6-140.jpg
---

图片和画布的建立、子图位置的布局
<!--more-->

{{< toc >}}

# 画图不显示
{{< codeblock "archives.py" "python" "http://underscorejs.org/#compact" "archives.py" >}}

plt.switch_backend('agg')
plt.switch_backend('QtAgg')
{{< /codeblock >}}

# 指定画布位置

{{< codeblock "archives.py" "python" "http://underscorejs.org/#compact" "archives.py" >}}
fig = plt.figure(figsize=(6,3),dpi=300)  
ax1 = fig.add_axes([0.08, 0.2, 0.9, 0.75])  # 图片左下角在长度上的百分比，图片左下角在宽度上的百分比，图片长度的百分比，图片高度的百分比
{{< /codeblock >}}

# 添加子图

{{< codeblock "archives.py" "python" "http://underscorejs.org/#compact" "archives.py" >}}
# 多张子图自动添加
for i in range(3):
		ax1 = fig.add_subplot(3, 1, i+1)  # 3行1列

# 共享坐标轴
fig.add_subplot(3, 1, 1, sharey=True)
figure,(ax1,ax2,ax3) = plt.subplots(1,3,figsize=(6,2),dpi=300, sharey=True)

# 双坐标轴
ax2 = ax1.twinx()
{{< /codeblock >}}

# 子图排版

{{< codeblock "archives.py" "python" "http://underscorejs.org/#compact" "archives.py" >}}
plt.subplots_adjust(wspace=0.5, hspace=0.5)

grid = plt.GridSpec(nrows=2, ncols=3, wspace=0.2, hspace=0.2)
ax1=plt.subplot(grid[0, 0])
ax2=plt.subplot(grid[0, 1:])

fig = plt.figure(figsize=(12,3), dpi=200)
grid = plt.GridSpec(nrows=1, ncols=10, wspace=0)
for n,x in enumerate(xticks):
    ax1=plt.subplot(grid[0, n])
{{< /codeblock >}}