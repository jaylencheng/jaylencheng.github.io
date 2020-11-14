---
#subtitle:   检测理论概述 #副标题
header-img: img/post-web.jpg    #这篇文章标题背景图片
catalog: true                       # 是否归档
tags:                               #标签
    - Information Theory
---

# Method of Types

## 1. Random variables and random sequences

We consder a diecrete random sequence with each of the variables $X$ in a finite alphabet $\mathcal{X}$ with probability distribution $P_X$. All of the $N$ variables are i.i.d., i.e., 

$$
X^n=(X_1, X_2,\cdots, X_n)
$$

$$
P_{X^n}(x^n)=\sum_{i=1}{n}P_{X_i}(x_i)
$$

$$
P_{X_i}(x_i)=P_X(x_i), \forall i=1,2,\cdots,n,\label{Equality}
$$

where we note $P_X: dom(X)\to [0,1]$ the distribution of $X$ , and ($\ref{Equality}$) indicates that all the possibiility of $X_i, \forall i=[N]$, is the same  as $P_{X_i}=P_X$. 

## 2. Empirical Distribution

For a given random sequence $x^n\in \mathcal{X}^n$, The number of appearances of a in the sequence:

$$
N(a|x^n)=\sum_{k=1}^{n}\delta_{x_i,a},\quad \forall a\in \mathcal{X}
$$

where $\delta_{a,b}$ is the Kronnekera symbol and returns 1 ony if $a=b$.  We denote:

$$
Q(a)=P_{x^n}(a)=\frac{1}{n}N(a|x^n), \label{Empirical}
$$

as the empirical distribution of any given $x^n$, and from $\ref{Empirical}$, empirical distribution $Q$ can also be seen as the frequency $P_{x^n}$.

## 3. Cross Entropy

For i.i.d. sequence $X^n$ with distribution $P_X$, and empirical distribution $P_{x^n}$ in a specific $x^n\in\mathcal{X}^n$, we calculate the $Pr(X^n=x^n)$.

$$
\frac{1}{n}logPr(X^n=x^n)\\=\frac{1}{n}log\prod_{i=1}^{n}P_X(x_i)\\=\frac{1}{n}log\prod_{a\in\mathcal{X}}P_X(a)^{N(a|x^n)}\\=\sum_{a\in\mathcal{X}}\frac{N(a|x^n)}{n}logP_X(a)\\=\sum_{a\in\mathcal{X}}Q(a)logP_X(a)
$$

This indicates that the probability of a random sequence only depends on the distribution of each random variable $X$ and the frequency of the value $x^n$. We define cross entropy:

$$
H(Q,P_X)=-\sum_{a\in\mathcal{X}}Q(a)logP_X(a), \label{crossentr}
$$

And 

$$
Pr(X^n=x^n)=q^{-nH(Q,P)}
$$

Easy to see that if all the frequency of  $a\in\mathcal{X}$ on different $x^n$s are the same, the values of probability distribution of $X^n$ on point $x^n$s are the same. This allows us to divide the sample space $\mathcal{X}^n$ into different parts and each part has the same empirical distribution, and automatically uniformly distributed. Any part is determined only by $Q: |\mathcal{X}|\to \frac{[n]}{n}$.

$$
\mathcal{T}_Q^n=\{x^n\in X^n|P_{x^n}=Q\}
$$

And we call any of these parts a type, and any type $\mathcal{T}_Q^n \subseteq \mathcal{X}^n$ is a set of sequences whose probability are numberially the same.  By combinatorial theory, the number of types is the munber of possible empirical distributions:

$$
\binom{n+|\mathcal{X}|+1}{n}\leq (n+1)^{|\mathcal{X}|}
$$

which is a ploynomial of n, and often be omitted  in exponentially perspective.

## 4. Size of Type

The size of any type can be shown combinatorially:

$$
|\mathcal{T}_Q^n|=\frac{n!}{\prod_{a\in\mathcal{X}}[nQ(a)]!}
$$

and noticing the Stirling approximation：

$$
n^n\sim n!e^n\to \frac{1}{n}lnn!\sim ln n-1,\quad n\to \infty
$$

We have:

$$
\frac{1}{n}log|\mathcal{T}_Q^n|\\\sim(lnn-1)-\sum_{a\in \mathcal{X}}Q(a)(ln[nQ(a)]-1)\\=(lnn-1)-(lnn-1)\sum_{a\in\mathcal{X}}Q(a)-\sum_{a\in\mathcal{X}}Q(a)logQ(a)\\=-\sum_{a\in\mathcal{X}}Q(a)logQ(a)=H(Q,Q), \label{entr}
$$

The size of type only depends on the empirical distribution $Q=P_{x^n}$, and we denote:

$$
H(Q)=H(Q,Q)=-\sum_{a\in\mathcal{X}}Q(a)logQ(a)
$$

as the entropy of a given distribution $Q$ .

It is worth noticing that $\frac{1}{n} \log|\mathcal{T}_Q^n|\sim H(Q)$ is an exponential approximation, which allows an error of a ploynomial times of the size. Specifically, for $\mathcal{T}_Q^n$ with $Q$ happens to be the distribution of $X$, i.e., $Q=P_X$, 

$$
\frac{1}{\binom{n+|\mathcal{X}|+1}{n}} \leq \sum_{x^n\in\mathcal{T}_Q^n}\prod_{i=1}^{n}P_{X}(x_i)=Q^n(\mathcal{T}_Q^n)\leq 1
$$

and by $\ref{crossentr}$, $\forall x^n\in \mathcal{T}_Q^n, P_{X^n}(x^n)=Q^n(x^n)=q^{-nH(Q)}$. So, we get the two-side bounds of the size of types:

$$
\frac{q^{nH(Q)}}{\binom{n+|\mathcal{X}|+1}{n}} \leq |\mathcal{T}_Q^n|\leq q^{nH(Q)}, \label{specsize}
$$

## 5. Probability of a type

We can simply calculate athe probability of any given type $\mathcal{T}_Q^n$ by the multiplication of the probability of any point in the type(as thay are uniformly distributed) and the size of the type, which is given in $\ref{crossentr}$ and $\ref{entr}$:

$$
\frac{1}{n}logP_{X^n}(\mathcal{T}_Q^n)\\=\frac{1}{n}log[|\mathcal{T}_Q^n|P_{X^n}(x^n:x^n\in \mathcal{T}_Q^n)]\\\sim\frac{1}{n}log|\mathcal{T}_Q^n|+\frac{1}{n}logP_{X^n}(x^n:P_{x^n}=Q)\\=H(Q)-H(Q,P_X), \label{relativeentr}
$$

We denote 

$$
H(Q,P_X)-H(Q)=D(Q||P_X)=-\sum_{a\in\mathcal{X}}P_X(a)log\frac{P_X(a)}{Q(a)}=D(Q||P_X)\geq 0
$$

as the Kullback-Liebler Divergence (or relative entropy). To put it more specifically from  $\ref{specsize}$,

$$
\frac{q^{nD(Q||P_X)}}{\binom{n+|\mathcal{X}|+1}{n}}\leq P_{X^n}(\mathcal{T}_Q^n)=|\mathcal{T}_Q^n|P_{X^n}(x^n:x^n\in \mathcal{T}_Q^n)\leq q^{nD(Q||P_X)}
$$

The above shows that the difference between $H(Q)$ and $H(Q,P_X)$ (i.e., the difference of empirical distribution and real distribution) determines the probability of a certain type. (Compared to the size of a type, which is only determined by the empirical distribution). We can intuitively cosnsider $ D(Q||P_X) $ as the "distance" between 2 distributions. The large distance of $Q$ and $P_X$, the less $P_{X^n}(\mathcal{T}_Q^n)$ will be. As a specific case when $P=Q$, $D(Q||P_X)=0$ and the probability gets maximum.

## 6. Typical Set

Although it seems that when $P=Q$ , $\frac{1}{n}logP_{X^n}(\mathcal{T}_Q^n)\sim 0$ , but  $P_{X^n}(\mathcal{T}_Q^n)\sim1\\$ is not correct as the former approximation is in a exponential sense. In fact, when  $n\to \infty$  , the number of types "near" $P_X$, say, $|Q-P_X|\leq \delta$ , is no less than $2n\delta$ with nearly (the difference will be bounded in the following statement) the same probability, so the probability of type $P_{X^n}(\mathcal{T}_{Q}^n)\leq P_{X^n}(\mathcal{T}_{P_X}^n)\leq 1/2n\delta\to 0, \quad n\to \infty$. So we  do not care any possibility of any <u>certain type</u> but a <u>range of types</u>. In this section we instructs that the possibility concentrates exactly around the maximum type $\mathcal{T}_{P_X}^n$. We define the range as the union of all "near maximum" types:

$$
\mathcal{T}_{[Q]_\delta}^n=\{x^n\in\mathcal{X}^n||Q(a)-P_{X}(a)|\leq\delta,\forall a\in \mathcal{X}\}\\
=\bigcup_{Q:|Q(a)-P_X(a)|\leq\delta,\forall a\in \mathcal{X}}\mathcal{T}_Q^n
$$

and we call it the <u>Typical Set</u>， and 

$$
\mathcal{T}_{[Q]_\delta}^{nC}=\overline{\mathcal{T}_{[Q]_\delta}^n}=\{x^n\in\mathcal{X}^n|\exists a\in \mathcal{X}, |Q(a)-P_{X}(a)|\geq\delta\}\\
=\bigcup_{Q:\exists a\in \mathcal{X}, |Q(a)-P_{X}(a)|\geq\delta}\mathcal{T}_Q^n
$$

an <u>Atypical Set</u>. We choose $\delta_{\epsilon}$ to make $|H(Q)-H(P_X)|\leq \epsilon$ . We can find such a $\delta_{\epsilon}$ due to the continuity of function:

$$
H(Q)=-\sum_{a\in\mathcal{X}}Q(a)logQ(a),\quad \\
H:\{(q_1,\cdots,q_{|\mathcal{X}|})|\forall i\in[n], q_i\in [0,1],\sum_{i=1}^{|\mathcal{X}|}q_i=1\}\to\mathbb{R}
$$

and thus 

$$
\forall \epsilon >0, \exists \delta_1>0,|(q_1,\cdots,q_{|\mathcal{X}|})-(p_1,\cdots,p_{|\mathcal{X}|})|\leq \delta_1\to |H(Q)-H(P_X)|\leq \epsilon
$$

where $(p_1,\cdots,p_{|\mathcal{X}|})$ is the list of probabilities in distribution $P_X$. We pick

$$
\delta_{\epsilon}=min\{\frac{\epsilon}{-\sum_{a\in \mathcal{X}}logP_X(a)},\frac{\epsilon}{-\sum_{a\in \mathcal{X}}logQ(a)}\}
$$

and $H(Q)$ is bounded by:

$$
H(Q)\leq H(Q,P_X)=-\sum_{a\in\mathcal{X}}Q(a)logP_X(a)\\
\leq -\sum_{a\in\mathcal{X}}(P_X(a)+\delta_\epsilon)logP_X(a)\\
\leq-\delta_\epsilon\sum_{a\in\mathcal{X}}logP_X(a)-\sum_{a\in\mathcal{X}}P_X(a)logP_X(a)\\
=\epsilon+H(P_X)
$$

and

$$
H(Q)=-\sum_{a\in\mathcal{X}}Q(a)logQ(a)\\
\geq -\sum_{a\in\mathcal{X}}(P_X(a)-\delta_\epsilon)logQ(a)\\
\geq H(P_X)-\epsilon\frac{\sum_{a\in\mathcal{X}}logQ(a)}{\sum_{a\in\mathcal{X}}logQ(a)}\\
=H(P_X)-\epsilon
$$

$$
|Q(a)-P_{X}(a)|\leq\delta_{\epsilon},\forall a\in \mathcal{X}\\
\to|(q_1,\cdots,q_{|\mathcal{X}|})-(p_1,\cdots,p_{|\mathcal{X}|})|\leq \delta_1\to |H(Q)-H(P_X)|\leq \epsilon
$$

We calculate the upper bound of the size of typical set:

$$
\frac{1}{n}log|\mathcal{T}_{[Q]_{\delta_\epsilon}}^n|\\
=\frac{1}{n}log\sum_{Q:|Q(a)-P_X(a)|\leq\delta,\forall a\in \mathcal{X}}|\mathcal{T}_Q^n|\\ 
\leq \frac{1}{n}log\binom{n+|\mathcal{X}|-1}{n}+\max_{Q:|Q(a)-P_X(a)|\leq\delta,\forall a\in \mathcal{X}}\frac{1}{n}log|\mathcal{T}_{Q}^n|\\
=H(Q)\leq H(P_X)+\epsilon, \quad n\to\infty
$$

and the lower bound can be done by the same way:

$$
\frac{1}{n}log|\mathcal{T}_{[Q]_{\delta_\epsilon}}^n|\\
=\frac{1}{n}log\sum_{Q:|Q(a)-P_X(a)|\leq\delta_\epsilon,\forall a\in \mathcal{X}}|\mathcal{T}_Q^n|\\ 
\geq \min_{Q:|Q(a)-P_X(a)|\leq\delta_\epsilon,\forall a\in \mathcal{X}}\frac{1}{n}log|\mathcal{T}_{Q}^n|\\
=H(Q)\geq H(P_X)-\epsilon, \quad n\to\infty
$$

for all types $\mathcal{T}_Q^n\subseteq \mathcal{T}_{[Q]_{\delta_{\epsilon}}}^{nC}$  , $\exists a \in \mathcal{X}, |Q(a)-P_X(a)|\geq \delta_{\epsilon}$. Due to the continuity and monotony of $f(p)=logp$ , that:

$$
|H(Q,Q)-H(P_X,Q)|=D(Q||P_X)\\
\geq Q(a)(logP_X(a)-logQ(a))\\
=Q(a)\frac{d(logp)}{dp}|_{p=Q(a)}[P_X(a)-Q(a)]\\
= Q(a)\frac{1}{Q(a)}\delta_\epsilon=\delta_\epsilon> 0
$$

Here we give the upper bound of atypical set:

$$
\frac{1}{n}logPr(X^n\in\mathcal{T}_{[Q]_{\delta_\epsilon}}^{nC})\\
=\frac{1}{n}log\sum_{Q:\exists a\in \mathcal{X}, |Q(a)-P_{X}(a)|\geq\delta_\epsilon}|\mathcal{T}_Q^n|\\
\leq \frac{1}{n}log\binom{n+|\mathcal{X}|-1}{n}+\max_{Q:|Q(a)-P_X(a)|\leq\delta,\forall a\in \mathcal{X}}\frac{1}{n}logPr(X^n\in\mathcal{T}_{Q}^{n})\\
=-D(Q||P_X)\leq -\delta_\epsilon, \label{proaty}
$$

To summarize the properties of typical set, it is worth noticing that the size of typical set:

$$
exp(n(H(P_X)+\epsilon))\leq |\mathcal{T}_{[Q]_\delta}^n|\leq exp(n(H(P_X)+\epsilon))
$$

which is exponentially small conpared with the whole size $\binom{n+|\mathcal{X}|-1}{n}$.  Each of the points in the typical set is nearly uniformly distributed, i.e., 

$$
H(P)-\epsilon\leq H(Q)\leq H(P)+\epsilon
$$

and the probability in this exponentially small area is numerally tend to $1$:

$$
P_{X^n}(\mathcal{T}_{[Q]_\delta}^n)=1-exp(-n\eta)
$$

At last we need to get a proper $\epsilon$ to make both $\epsilon$ itself be sufficiently small and $n\eta=n\delta_{\epsilon}$ sufficiently large. For example, $\epsilon=n^p$ with $p\in[-1,0]$ is a proper setting.

## 7. Substantial Set

A set $\mathcal{A}\in \mathcal{X}^n$ is called a substantial set iff 

$$
Pr(X^n\in\mathcal{A})=\mu>0
$$

and intuitively, the positive probability can only be valued in the typical set when $n\to \infty$, as ($\ref{proaty}$) shows that :

$$
Pr(X^n\in\mathcal{T}_{[Q]_{\delta_\epsilon}}^{nC})\to 0,\quad n\to \infty
$$

To show this, we first calculate the probability of  intersection of $\mathcal{A}$ and typical set:

$$
Pr(X^n\in \mathcal{A}\cap \mathcal{T}_{[Q]_\delta}^n)=1-Pr(\overline{\mathcal{A}}\cup \mathcal{T}_{[Q]_{\delta_\epsilon}}^{nC})\\
\geq 1-Pr(X^n\in \overline{\mathcal{A}})-Pr(X^n\in \mathcal{T}_{[Q]_{\delta_\epsilon}}^{nC})\\
\geq 1-(1-\mu)-exp^{-n\delta_\epsilon}\to \mu,\quad n\to \infty
$$

so the probability almostly distributed in the typical set. We can calculate a lower bound of $\mathcal{A}$ by the property that the distribution in a typical set is uniform:

$$
\frac{1}{n}log|\mathcal{A}|\geq \frac{1}{n}log|\mathcal{A}\cap \mathcal{T}_{[Q]_\delta}^n|\\
\geq \frac{1}{n}log(\mu-exp(-n\delta))+H(P)-\epsilon\\
\to H(P)-\epsilon,\quad n\to \infty
$$
