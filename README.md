# SA-TSP
> 使用模拟退火算法(SA)解决TSP问题(java)
> 
> 可用于解决厦门大学计算智能作业

## 解题思路
一开始设定一个由全部城市编号组成的路径排列，以及退火算法需要的各类参数，如马尔可夫链长度、衰减参数、衰减参数下降参数、当前温度和终止温度，然后随着每次降温，进行解的更新衰减参数下降参数，以一定概率的接受效果差的解，最后当温度降到终止温度时，即停止解的搜索。

## 方法实现
先确定初始状态，然后开始降温循环，每次循环都需要进行多次迭代，每次迭代都要以一定扰动生成一个新状态，按照蒙特卡洛准则判断是否接受新状态，如可接受则更新状态，否则保留原有状态，同温度下全部迭代完成后更新蒙特卡洛准则中的温度，依据初始参数中的衰减参数进行降温，同时也要依据初始参数中的衰减参数下降参数更新衰减参数的值，继续迭代，直到当前温度不大于终止温度时停止算法，然后输出获得的最短路线。
其中每次迭代中的扰动方式以轮盘赌的方式随机以下方法的其中一种进行扰动:
- 交换结构
  - 若有 6 个城市，当前解为 123456，我们随机选择两个位置，然后将这两个位置上的元素进行交换。比如说，交换 2 和 5 两个位置上的元素，则交换后的解为 153426。
- 逆转结构
  - 若有 6 个城市，当前解为 123456，我们随机选择两个位置，然后将这两个位置之间的元素进行逆序排列。比如说，逆转 2 和 5 之间的所有元素，则逆转后的解为 154326。
- 插入结构
  - 若有 6 个城市，当前解为 123456，我们随机选择两个位置，然后将这第一个位置上的元素插入到第二个元素后面。比如说，第一个选择 2 这个位置，第二个选择 5 这个位置，则插入后的解为134526。

## 求解结果
本问题求解结果：最短回路长度为699，路径为1,2,3,4,...,41,42,1

## 注意
为了提高精度的同时加快算法末期的精度，本算法中加入了衰减参数下降参数的衰减参数，即每轮迭代衰减参数都会乘上一个衰减系数，这样可以在不丢失精度的同时加快算法速度。
