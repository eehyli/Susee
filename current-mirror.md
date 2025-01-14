
# A、基本电流镜
## 一、搭建电路
对于基本电流镜，忽略沟道长度调制时，输出电流与输入电流有如下关系式：
$$Iout=\frac{(W/L)_2}{(W/L)_1}I_{REF}

$$
搭建基本电流镜电路，其中电流源的器件名为idc，设置两边nmos的W/L相等，这样就能使输出电流和输入电流相等。如下图所示：
![text](https://github.com/dailiuyao/markdown-photos/blob/master/current%20mirror/schematic.png)
![text](https://github.com/dailiuyao/markdown-photos/blob/master/current%20mirror/idc.png)
![text](https://github.com/dailiuyao/markdown-photos/blob/master/current%20mirror/vdc.png)

## 二、变量设置
点击variables，单击copy from，选择vout，并赋值1，如下图：
![text](https://github.com/dailiuyao/markdown-photos/blob/master/current%20mirror/variables.png)

## 三、仿真模式
check and save后，选择ADE L,选择analyses，进行仿真模式设置，如下图：
![text](https://github.com/dailiuyao/markdown-photos/blob/master/current%20mirror/analyses.png)

## 四、输出设置
选择输出变量，注意输出变量若为电流，则一定要选择电路图中的节点（若是电压则选择电线），如下图所示：
![text](https://github.com/dailiuyao/markdown-photos/blob/master/current%20mirror/outputs.png)

## 五、仿真结果
运行仿真，输出结果如图，可观察出此电流镜的输出端阈值电压在0.6v左右，如下图：
![text](https://github.com/dailiuyao/markdown-photos/blob/master/current%20mirror/%E4%BB%BF%E7%9C%9F%E7%BB%93%E6%9E%9C.png)

# B、共源共栅电流镜
## 一、搭建电路cascode电路可以有效的抑制沟道长度调制效应，因为共源共栅器件可以使底部晶体管免受输出端电压变化的影响，如果$$$\frac{(W/L)_3}{(W/L)_4}=\frac{(W/L)_1}{(W/L)_2}$$$,则$$$V_{GS3}=V_{GS4},V_X=V_Y$$$.但一般的共源共栅电流镜的输出电压比最低电压高了一个阈值电压，这是因为一般的$$$V_{DS2}=V_{GS2}$$$,但$$$V_{DS2}$$$最低可以等于$$$V_{GS2}-V_{TH}$$$。在低压共源共栅电流镜中，b处的电压最低可以等于$$$V_{GS4}+V_{GS2}-V_{TH}$$$,此时电压余度最小。
搭建cascode电路，其中idc均等于100uA，输出端vdc中DC=1V,ACM=1V，如下图所示：
![text](https://github.com/dailiuyao/markdown-photos/blob/master/cascode/%E7%94%B5%E8%B7%AF1.png)

## 二、仿真模式
搭建电路完毕后，进入仿真界面，选择AC仿真，如下图：
![text](https://github.com/dailiuyao/markdown-photos/blob/master/cascode/analysis.png)

## 三、输出设置
在输出量选择窗口中，选择VDC的下节点和所连导线，设置输出量为Vout与Iout。如下图所示：
![text](https://github.com/dailiuyao/markdown-photos/blob/master/cascode/outputs.png)

## 四、仿真结果
运行仿真，输出Vout与Iout，在结果输出页面选择计算器图标，在计算器页面的输入框上方勾选wave，并在单击输入框，待光标出现后在曲线图页面单击Vout线，再单击Iout线，回到计算器页面，单击除号/，由此可得输出阻抗的代数表达式，再单击输出框上方的evaluate the buffer，输出阻抗仿真图。
仿真结果一：
![text](https://github.com/dailiuyao/markdown-photos/blob/master/cascode/%E4%BB%BF%E7%9C%9F%E7%BB%93%E6%9E%9C%E4%B8%802.png)
图中上线是输出电流，下线是输出电压。
选择Vout：
![text](https://github.com/dailiuyao/markdown-photos/blob/master/cascode/%E9%80%89%E6%8B%A9Vout.png)
选择Iout：
![text](https://github.com/dailiuyao/markdown-photos/blob/master/cascode/%E9%80%89%E6%8B%A9Iout.png)
输出阻抗表达式：
![text](https://github.com/dailiuyao/markdown-photos/blob/master/cascode/VOUT-IOUT.png)
输出阻抗仿真图：
![text](https://github.com/dailiuyao/markdown-photos/blob/master/cascode/%E4%BB%BF%E7%9C%9F%E7%BB%93%E6%9E%9C%E4%BA%8C1.png)
图中上线是输出电流，中线是输出电压，下线是输出阻抗。
