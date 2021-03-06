# EulerGraph

离散数学上机实验4：图的随机生成及欧拉（回）路的确定

## 实验目的：
编程随机生成n个结点的无向图并能进行（半）欧拉图的判定，若是则给出欧拉（回）路。

## 要求：
1. 对给定n个结点，随机生成邻接矩阵以确定某无向简单图并进行欧拉图和半欧拉图的判定
2. 若符合，则给出至少一条欧拉回路或欧拉路

## 实验原理及内容：
* 原始输入数据只有一个N，所有只能随机填充无向图了
* 填充一个矩阵的上半阶梯（主对角线以上的部分），然后将上半部分翻转复制到下半部分
* 遍历每行查找值为1的点数来确定每个点的度，并获取总度数
* 利用（半）欧拉图的性质来判断是否存在欧拉（回）路
* 若存在，则对图进行遍历并删边，直到度为0，输出路径

## Tips：
1. 因为无向图每个节点的度=入度+出度，因此总度数为节点度数之和除2
2. 因为关系阵是随机获取的，所以**并不能保证**每次生成的图都有欧拉（回）路，理论上节点个数越多每次获取的图是（半）欧拉图的概率就越低，需要多次重复尝试
3. 欧拉（回）路的路径查找没有使用深度优先搜索而是采用了一种更为简单粗暴的方法，但对于**只需要一个解**的问题要求应该说也是**够用**的~~（有效测试了20回左右目前还没有遇到过走不通的情况）~~
4. 为了确保正确，在主函数后保留了一次输出，用于输出删边之后的关系阵和度数，理论上应该全部是0。如不需要将`main.cpp`中的第**14**行删掉即可