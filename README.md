## Bowyer-Watson

### 算法原理

Bowyer-Watson算法是逐点插入算法，每次插入后分割插入点所在的三角形，如下图：

![insert](/assets/insert.jpg)

之后检查相邻三角形是否满足Delaunay三角网格条件，如果不满足则通过交换四边形对角线完成插入，如下图：

![update](/assets/update.jpg)

为了保持算法的连贯性，在初始时使用一个包含所有点空间的矩形和一条对角线作为初始三角网格，并在最后删除。

### 实现思路

这里使用Java实现了此算法。

由于三角形最多只有三个相邻三角形（共用一条边），因此可以将三角网格储存为链表结构。并且三角形需要具有外接圆属性，并且能够判断给定点是否在三角形内或是外接圆内。

```java
class mTriangle{
    dPoint a;
    dPoint b;
    dPoint c;
    dPoint center;
    double Rsq;
    /** share points a&b*/
    int neighbor1;
    /** share points b&c*/
    int neighbor2;
    /** share points c&a*/
    int neighbor3;
    public mTriangle(dPoint p1, dPoint p2, dPoint p3)
    /* calculate External circle center*/
    protected void getCenter()
    /* judge if p is in triangle */
    public boolean inTriangle(dPoint p)
    public boolean inExternalCircle(dPoint p)
}
```
具体实现见/src/Delaunay.java

### 效果示例

以添加五个点为例，下图为网格更新的流程

![](/assets/seq.gif)

