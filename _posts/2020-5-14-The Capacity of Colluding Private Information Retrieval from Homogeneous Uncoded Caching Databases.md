---
#subtitle:   检测理论概述 #副标题
header-img: img/post1.jpg    #这篇文章标题背景图片
catalog: true                       # 是否归档
tags:                               #标签
    - 信息与通信
    - 信息论
    - Private Information Retrieval
  
---



# 1. Achievability
We note the lower bound of storage constrained PIR with $\mu$ storage coefficient. We have:

$$
\begin{align}
D\geq&L+\dfrac{1}{2}\sum_{k=1}^{2}\sum_{\mathcal{S}:|\mathcal{S}|= 1}|W_{k,\mathcal{S}}|L+\dfrac{5}{12}\sum_{k=1}^{2}\sum_{\mathcal{S}:|\mathcal{S}|= 2}|W_{k,\mathcal{S}}|L+\dfrac{1}{3}\sum_{k=1}^{2}\sum_{\mathcal{S}:|\mathcal{S}|= 3}|W_{k,\mathcal{S}}|L\\
=&L+\sum_{\mathcal{S}:|\mathcal{S}|= 1}\alpha_{\mathcal{S}}+\dfrac{5}{6}\sum_{\mathcal{S}:|\mathcal{S}|= 2}\alpha_{\mathcal{S}}+\dfrac{2}{3}\sum_{\mathcal{S}:|\mathcal{S}|= 3}\alpha_{\mathcal{S}}\\
=&2\sum_{\mathcal{S}:|\mathcal{S}|= 1}\alpha_{\mathcal{S}}+\dfrac{11}{6}\sum_{\mathcal{S}:|\mathcal{S}|= 2}\alpha_{\mathcal{S}}+\dfrac{5}{3}\sum_{\mathcal{S}:|\mathcal{S}|= 3}\alpha_{\mathcal{S}}
\end{align}
$$

which is equivalent to the following linear problem:

$$
\begin{align}
\min_{\alpha_{\mathcal{S}}\geq 0} \quad &2(\alpha_1+\alpha_2+\alpha_3)+\dfrac{11}{6}(\alpha_{1,2}+\alpha_{2,3}+\alpha_{1,3})+\dfrac{5}{3}\alpha_{1,2,3} \\
s.t. \quad & \alpha_1+\alpha_2+\alpha_3+\alpha_{1,2}+\alpha_{2,3}+\alpha_{1,3}+\alpha_{1,2,3}=1 \\
&\alpha_1+\alpha_{1,2}+\alpha_{1,3}+\alpha_{1,2,3} \leq \mu\\
&\alpha_2+\alpha_{1,2}+\alpha_{2,3}+\alpha_{1,2,3} \leq \mu\\
&\alpha_3+\alpha_{2,3}+\alpha_{1,3}+\alpha_{1,2,3} \leq \mu\\
\end{align}$$

the fractions are all easy according to TPIR scheme and memory sharing scheme. Every $\alpha_{1,2,3},\alpha_{1,2},\alpha_{1}$ sums are all achievable values. In fact we can figure out the coefficients in the following CONVERSE result:

$$
\begin{equation}
	x\sum_{k=1}^{2}H(W_k)+y\sum_{k=1}^{2}\sum_{i\neq k}H(W_k|Z_i)+z\sum_{k=1}^{2}H(W_k|Z_{[3]-\{k\}})
\end{equation}$$

via

$$
\begin{align}
&2x+4y+2z=2,\quad |\mathcal{S}|=1 \\
&2x+2y=\dfrac{11}{6},\quad |\mathcal{S}|=2 \\
&2x=\dfrac{1}{3},\quad |\mathcal{S}|=3 
\end{align}$$

and $(x,y,z)=(\dfrac{5}{6},\dfrac{1}{12},0)$

# 2.Converse

$$
\begin{align}
H(A_{[3]}^1|W_1)=&H(A_1^1,A_2^1|W_1)+H(A_3^1|A_1^1,A_2^1,W_1) 
\end{align}$$

by taking all possible permutation $(i,j,k)\sim(1,2,3)$ together,

$$
\begin{align}
6H(A_{[3]}^1|W_1)=&2(H(A_1^1,A_2^1|W_1)+H(A_1^1,A_3^1|W_1)+H(A_3^1,A_2^1|W_1))\\
&+2(H(A_3^1|A_1^1,A_2^1,W_1)+H(A_2^1|A_1^1,A_3^1,W_1)+H(A_1^1|A_2^1,A_3^1,W_1))
\end{align}$$

However, according to $(11)\sim(13)$, the ideal coefficient

$$
\begin{align}
D \geq &\dfrac{5}{6}\sum_{k=1}^{2}H(W_k)+\dfrac{1}{12}\sum_{k=1}^{2}\sum_{i\neq k}H(W_k|Z_i)\\
=&L+\dfrac{1}{3}\sum_{k=1}^{2}H(W_k)+\dfrac{1}{12}\sum_{k=1}^{2}\sum_{i\neq k}H(W_k|Z_i) 
\end{align}$$

which is equivalent to

$$
\begin{align}
6H(A_{[3]}^1|W_1) \geq &4H(W_2)+(H(W_2|Z_1)+H(W_2|Z_2)+H(W_2|Z_3)) \\
=&2(H(A_1^1,A_2^1|W_1)+H(A_1^1,A_3^1|W_1)+H(A_3^1,A_2^1|W_1))\\
&+(H(A_1^1,A_2^1|W_1,Z_3)+H(A_1^1,A_3^1|W_1,Z_2)+H(A_3^1,A_2^1|W_1,Z_1))
\end{align}$$

and

$$
\begin{align}
	&H(A_3^1|A_1^1,A_2^1,W_1)+H(A_1^1|A_2^1,A_3^1,W_1)\geq H(A_1^1,A_3^1|W_1,Z_2)=H(A_3^1|A_1^1,Z_2,W_1)+H(A_1^1|Z_2,W_1)\\
	\Leftrightarrow & I(A_1^1;A_3^1|Z_2,W_1)=0
\end{align}$$

# 3.System Model}

$$
\begin{equation}
(Data Constraint, DC1):\quad H(W_k)=L, H(W_{[K]})=KL;  k=1,\cdots,K
\end{equation}$$

$$
\begin{equation}
(DC2):\quad H(Z_n)\leq m_n KL,  \quad 0\leq m_n \leq 1 ;  n=1,\cdots,N;
\end{equation}$$

$$
\begin{equation}
(DC3):\quad W_k=\cup_{\mathcal{S}\subseteq [N]}W_{k,\mathcal{S}}, \quad H(W_{k,\mathcal{S}})=|W_{k,\mathcal{S}}|L;
\end{equation}$$

$$
\begin{equation}
(DC4):\quad \alpha_{\mathcal{S}}=\frac{1}{K}\sum_{k=1}^{K}|W_{k,\mathcal{S}}|, \quad m_n \geq \frac{1}{KL}H(Z_n)=\sum_{\mathcal{S}\subseteq [N],n\in \mathcal{S}}\alpha_{\mathcal{S}}, n\in [N];
\end{equation}$$

$$
\begin{equation}
(DC5):\quad 1=\frac{1}{KL}H(W_{[K]})=\frac{1}{KL}\sum_{k=1}^{K}\sum_{\mathcal{S}:|\mathcal{S}| \geq l}H(W_{k,\mathcal{S}})=\sum_{l=1}^{N}\binom{N}{l}\frac{1}{K\binom{N}{l}}\sum_{k=1}^{K}\sum_{\mathcal{S}:|\mathcal{S}|=l}|W_{k,\mathcal{S}}|=\sum_{l=1}^{N}\binom{N}{l}x_l;
\end{equation}$$

$$
\begin{equation}
(Query Constraint, QC):\quad I(W_{[K]};Q_{[N]}^k)=0 ,\quad k=1,\cdots,K;  n=1,\cdots,N;
\end{equation}$$

$$
\begin{equation}
(Answer Constraint, AC): \quad H(A_{n}^k|Q_{n}^k,Z_n)=0 ,\quad  k=1,\cdots,K;  n=1,\cdots,N;
\end{equation}$$

$$
\begin{equation}
(Correctness Constraint, CC): \quad H(W_k | A_{[N]}^k,Q_{[N]}^k)=0,\quad k=1,\cdots,K;
\end{equation}$$

$$
\begin{equation}
(Privacy Constraint, PC): \quad I(Q_{\mathcal{T}}^k , A_{\mathcal{T}}^k, W_{[K]};k)=0,  \quad \mathcal{T}\subseteq [N], |\mathcal{T}|=T, k=1,\cdots,K;
\end{equation}$$

$$
\begin{equation}
(Optimal Function): \quad D=\sum_{n=1}^{N}H(A_n^{k}), \quad C=sup\{\frac{L}{D}:(D,L)is \quad achievable\};
\end{equation}$$