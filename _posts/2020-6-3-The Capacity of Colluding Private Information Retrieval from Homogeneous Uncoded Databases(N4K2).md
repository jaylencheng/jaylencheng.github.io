---
#subtitle:   检测理论概述 #副标题
header-img: img/post1.jpg    #这篇文章标题背景图片
catalog: true                       # 是否归档
tags:                               #标签
    - 信息与通信
    - 信息论
    - Private Information Retrieval
  
---

We aim to prove that when N=4 and K=2, the capacity of pir with uncoded, homogeneous part-storage server.
# 1.Converse

We assume that:

$$
\begin{equation}
	3\sum_{\mathcal{S}:|\mathcal{S}|= 1}\alpha_{\mathcal{S}}-\sum_{\mathcal{S}:|\mathcal{S}|= 3}\alpha_{\mathcal{S}}\geq 0
\end{equation}$$

and we can get the lower bound of the downloads by:

$$
\begin{align}
&6D\\
\geq&6L+6H(A_{[4]}^1|W_1)\\
=&6L+(H(A_1^1,A_2^1|W_1)+H(A_1^1,A_3^1|W_1)+H(A_3^1,A_2^1|W_1)+\\
&H(A_1^1,A_4^1|W_1)+H(A_4^1,A_3^1|W_1)+H(A_4^1,A_2^1|W_1))\\
&+(H(A_4^1,A_3^1|A_1^1,A_2^1,W_1)+H(A_4^1,A_2^1|A_1^1,A_3^1,W_1)+H(A_4^1,A_1^1|A_2^1,A_3^1,W_1)\\
&+H(A_1^1,A_3^1|A_4^1,A_2^1,W_1)+H(A_1^1,A_2^1|A_4^1,A_3^1,W_1)+H(A_2^1,A_3^1|A_4^1,A_1^1,W_1))\\
=&6L+3H(W_k)+\sum_{\mathcal{B}\subseteq [4],|\mathcal{B}|=2}H(W_k|Z_{\mathcal{B}})\\
\end{align}$$

we take the realization of k by $k=1$ and $k=2$, we have:

$$
\begin{align}
6D\geq&6L+\dfrac{3}{2}\sum_{k=1}^{2}H(W_k)+\dfrac{1}{2}\sum_{k=1}^{2}\sum_{\mathcal{B}\subseteq [4]-{k},|\mathcal{B}|=2}H(W_k|Z_{\mathcal{B}})\\
=&\dfrac{5}{2}\sum_{\mathcal{S}:|\mathcal{S}|= 1}\alpha_{\mathcal{S}}+\dfrac{11}{6}\sum_{\mathcal{S}:|\mathcal{S}|= 2}\alpha_{\mathcal{S}}+\dfrac{3}{2}\sum_{\mathcal{S}:|\mathcal{S}|= 3}\alpha_{\mathcal{S}}+\dfrac{3}{2}\sum_{\mathcal{S}:|\mathcal{S}|= 4}\alpha_{\mathcal{S}}\\
\geq &2\sum_{\mathcal{S}:|\mathcal{S}|= 1}\alpha_{\mathcal{S}}+\dfrac{11}{6}\sum_{\mathcal{S}:|\mathcal{S}|= 2}\alpha_{\mathcal{S}}+\dfrac{5}{3}\sum_{\mathcal{S}:|\mathcal{S}|= 3}\alpha_{\mathcal{S}}+\dfrac{3}{2}\sum_{\mathcal{S}:|\mathcal{S}|= 4}\alpha_{\mathcal{S}}
\end{align}$$

# 2.Achievability
We note the lower bound of storage constrained PIR with $\mu$ storage coefficient. We have:

$$
\begin{align}
D\geq=&2\sum_{\mathcal{S}:|\mathcal{S}|= 1}\alpha_{\mathcal{S}}+\dfrac{11}{6}\sum_{\mathcal{S}:|\mathcal{S}|= 2}\alpha_{\mathcal{S}}+\dfrac{5}{3}\sum_{\mathcal{S}:|\mathcal{S}|= 3}\alpha_{\mathcal{S}}+\dfrac{3}{2}\sum_{\mathcal{S}:|\mathcal{S}|= 4}\alpha_{\mathcal{S}}
\end{align}$$

which is equivalent to the following linear problem:

$$
\begin{align}
\min_{\alpha_{\mathcal{S}}\geq 0} \quad &2(\alpha_1+\alpha_2+\alpha_3+\alpha_{4})\\	+&\dfrac{11}{6}(\alpha_{1,2}+\alpha_{2,3}+\alpha_{1,3}+\alpha_{1,4}+\alpha_{2,4}+\alpha_{4,3})\\
+&\dfrac{5}{3}(\alpha_{1,2,3}+\alpha_{1,2,4}+\alpha_{1,4,3})+\dfrac{3}{2}\alpha_{1,2,3,4} \\
s.t. \quad & \alpha_1+\alpha_2+\alpha_3+\alpha_{4}+\alpha_{1,2}+\alpha_{2,3}+\alpha_{1,3}+\alpha_{1,4}\\
&+\alpha_{2,4}+\alpha_{4,3}+\alpha_{1,2,3}+\alpha_{1,2,4}+\alpha_{1,4,3}+\alpha_{1,2,3,4}=1\\
&\alpha_1+\alpha_{1,2}+\alpha_{1,3+\alpha_{1,4}}+\alpha_{1,2,3}+\alpha_{1,2,4}+\alpha_{1,4,3}+\alpha_{1,2,3,4} \leq \mu\\
&\alpha_2+\alpha_{1,2}+\alpha_{2,3}+\alpha_{2,4}++\alpha_{4,2,3}+\alpha_{1,2,3}+\alpha_{1,2,4}+\alpha_{1,2,3,4} \leq \mu\\
&\alpha_3+\alpha_{2,3}+\alpha_{1,3}+\alpha_{4,3}+\alpha_{1,2,3}+\alpha_{4,2,3}+\alpha_{1,4,3} \leq \mu
\end{align}$$

the fractions are all easy according to TPIR scheme and memory sharing scheme. Every $\alpha_{1,2,3,4},\alpha_{1,2,3},\alpha_{1,2},\alpha_{1}$ sums are all achievable values.
。。