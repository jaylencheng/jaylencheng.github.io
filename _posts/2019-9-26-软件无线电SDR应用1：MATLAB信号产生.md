@[TOC](软件无线电SDR应用（1）MATLAB信号产生)

# MATLAB简介

本系列利用MATLAB和Verilog语言进行软件无线电开发。MATLAB的主要优势体现在以下方面：

1.**友好的工作平台和编程环境**
2.**简单易用的程序语言**
3.**强大的科学计算处理能力**
4.**出色的图形处理能力**
5.**应用广泛的集合模块工具**
6.**实用的程序接口平台**
7.**包括用户界面的软件开发**

# 常用信号产生函数
**分三类**
	*内部函数*
	*工具箱里封装的函数*
	*自己写的函数*
	
`rand(m,n)`:产生[0，1]时域均匀分布序列
`randn(m,n)`：产生[0，1]频域均匀分布序列，即1W白噪声（零均值，1方差）
`square(T)`:T为周期，1为幅值的方波
`square(T，DUTY)`:T为周期，1为幅值的方波，DUTY占空比，设为0~100，默认50
`sawtooth(T,width)`T为周期，宽度为width的三角波
`sin sinh asin asinh cos cosh acos acosh tan cot tanh coth`是T为周期，1为幅值的

下面为一例子：
```javascript
%产生方波、正弦波和三角波
psin=10;
pnoise=1;
f=100;
fs=1000;
width=0.5;
duty1=50;
duty2=75;
duty3=25;

%% wavegenerator
t=0:1/fs:0.1;
c=2*pi*f*t;
sq=square(c);
sq1=square(c,duty1);
sq2=square(c,duty2);
sq3=square(c,duty3);
tr=sawtooth(c,width);
si=sin(c);

%% 随机信号
noi=rand(1,length(t));
noise=randn(1,length(t));
sin_noise=sqrt(2*psin)*si+sqrt(pnoise)*noise;
sin_noise_gui1=sin_noise/max(sin_noise);

%% draw
subplot(4,2,1);plot(t,sq);
subplot(4,2,2);plot(t,sq1);
subplot(4,2,3);plot(t,sq2);
subplot(4,2,4);plot(t,sq3);
subplot(4,2,5);plot(t,tr);
subplot(4,2,6);plot(t,noi);
subplot(4,2,7);plot(t,noise);
subplot(4,2,8);plot(t,sin_noise);

```
结果如图：
![结果](https://img-blog.csdnimg.cn/20190510143634724.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQwMDkwODU5,size_16,color_FFFFFF,t_70)

# 常用信号处理和滤波函数
## 滤波函数filter
任何一个离散系统都可以看成是一个数字滤波器，系统输出就是输入信号经过滤波后的结果。
filter涉及离散时间系统的系统函数。对于一个N阶系统而言，其系统函数可以表示为：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190512010249217.png)
差分方程：
![在这里插入图片描述](https://img-blog.csdnimg.cn/201905120103193.png)
由此，将a,b各元素从小到大排列（a0=1）可以得到唯一的行向量a,b，其确定了唯一的离散时间系统。
## 单位抽样响应函数impz
`impz（b,a,p）`:确定了由分子向量、分母向量和点数p得到的单位抽样相应的输出向量。不设p值将默认。绘出杆图
`h=impz（b,a,p）`:确定了由分子向量、分母向量和点数p得到的单位抽样相应的输出向量。不设p值将默认。将单位抽样响应向量保存于h中

## 单位滤波函数freqz
`freqz（b,a,x）`:确定了由分子向量、分母向量和输入得到的输出向量。由此得到x经过滤波器滤波后的输出结果。
`filter（b,a,x）`:确定了由分子向量、分母向量和输入得到的输出向量。由此得到x经过滤波器滤波后的输出结果。
