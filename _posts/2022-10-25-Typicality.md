---
#subtitle:   检测理论概述 #副标题
header-img: img/post-web.jpg    #这篇文章标题背景图片
catalog: true                       # 是否归档
tags:                               #标签
    - Information Theory
---

# Typicality
In 0-error data compression, we proved that the infimum of expected length of codewords is equal to the entropy. We go further to explore entropy in therms of the asymptotic behavior of i.i.d. sequences, known as the **Asymptotic Equipartition Property** (AEP).
	
We consder a diecrete random sequence with each of the variables $X_k, k\geq 1$ in a finite alphabet $\mathcal{X}$ with probability distribution $p_X$. All of the $N$ variables are i.i.d., i.e., 


$$
\begin{align}

X^n&=(X_1, X_2,\cdots, X_n)\\
p_{X^n}(x^n)&=\prod_{i=1}^{n}p_{X_i}(x_i)\\
p_{X_i}(x_i)&=p_X(x_i), \forall i=1,2,\cdots,n,
\end{align}
$$
<span id="Equality">sad</span>

where we note $p_X: \mathcal{X}\to [0,1]$ the distribution of $X$ , and ([here](#Equality)) indicates that all the possibiility of $X_i, \forall i=[N]$, is the same  as $P_{X_i}=P_X$.* Note: In the following relations, we use $ P_X $ to denote the distribution of any $ X $ (rather than $ X^n $), and do not care whose distribution it is.

In the context, the logarithms are in the base 2 by default.

## Equality and Convergence of RV
 There are several senses that 2RVs can be considered to be equivalent. 
 
**Definition 1:**
 	(Equivalence of RVs):\\
 	Let $ X,Y $ be 2 RVs. We say $ X $ and $ Y $ are:
 	
*  equal in distribution (denoted $ X\stackrel{d}{=}Y $) iff they have the same CDF:  

$$
\begin{align}

	Pr\{X\leq x\}=Pr\{Y\leq x\},\quad \forall x\in \mathcal{X}
\end{align}
$$

*  equal almost surely (denoted $ X\stackrel{a.s.}{=}Y $) iff $ Pr\{X\neq Y\}=0 $.
*  equal iff $ X(\omega)=Y(\omega),\quad \forall \omega\in\Omega $.
 	
\#

* Note: For practical purpose, the measure spaces of $ X $ and $ Y $ are rarely explicitly characterized, so real equality is the least useful while the notion of almost sure equality is as strong as the actual equality.

**Lemma 1:**Let $ X,Y $ be RVs.\\
 	1. $ M_X(t)=M_Y(t),\forall t\in \mathbb{R} $, then $ X\stackrel{d}{=}Y $.\\
 	2. $ X\stackrel{a.s.}{=}Y\iff d_{\infty}(X;Y)\stackrel{\Delta}{=} \text{ess }\sup_{\omega}|X(\omega)-Y(\omega)|=0 $.
 \#

The convergence of RV describes that a sequence of essentially random or unpredictable events (characterized by  $ \{X_n\}_{n\in\mathbb{N}_+} $) can be settled into patterns that are intuitively unchanging.

**Definition 2:**
	(Convergence in Distribution):\\
A sequence $ X_1,X_2,\cdots $ of RVs is said to converge in distribution, or converge weakly to a RV $ X $, denoted $ X_n\stackrel{d}{\to}X $, or $ X_n \Rightarrow X $ iff $ \lim\limits_{n\to\infty} F_{X_n}(x)=F_X(x)$ holds for all $ x\in\mathcal{X} $ at which $ F_X $ is continuous.
\#
The constraints on continuous points are essential. Here is a counterexample:

**Example 1:**
Consider $ \{X_n\}_{n\in\mathbb{N}_+} $ that $ X_n\sim U([1,1/n]) $ then the CDF converges to a degenerate RV $ X=0 $. The contradictory is that $ F_X(0)=1 $ while $ \forall n\in\mathbb{N}_+,\quad F_{X_n}(0)=0 $, not convergence at the discontinuous point $ x=0 $.
\# 

weak convergence do not talk about the independence or correlated relations. Here are some lemmas related:

**Lemma 2:**
	(Scheff's lemma): Let $ f_n $ a sequence of integrable function on a measure space $ (X,\Sigma,\mu) $ that converges a.e. to another integrable function $ f $, then:
	

$$
\begin{align}

	\int |f_n-f|d\mu\to 0\iff \int |f_n|d\mu \to\int |f|d\mu
	\end{align}
$$

So the a.e. pointwise convergence in PDF implies convergence in distribution.
\#
* Note: The counterpart is not true. Consider $ f_{X_n}(x)=(1-\cos(2n\pi x) )I_{[0,1]}(x) $ where $ I_A $ is the indicator function of $ A $. Then $ X_n\stackrel{d}{\to}X\sim U([0,1]) $ while the PDF shows no convergence. 


**Lemma 3:**
	(Levy's continuity theorem):\\ 
	The sequence $ \{X_n\} $ converges in distribution to $ X $ iff the sequence of corresponding characteristic functions $ \{\phi_n\} $ converges pointwise to the characteristic function $ \phi $ of $ X $.
\#

**Definition 3:**
	(Convergence in Probability):\\
	A sequence $ X_1,X_2,\cdots $ of RVs is said to converge in probability to a RV $ X $, denoted $ X_n\stackrel{p}{\to}X $ iff 

$$
\begin{align}

	\forall \delta>0,\quad \lim\limits_{n\to\infty} Pr\{|X_n-X|>\delta\}=0
	\end{align}
$$

\#
* Note: for metric space, it is $ \forall \delta>0,\quad \lim\limits_{n\to\infty} Pr\{d(X_n-X)>\delta\}=0 $.}


**Lemma 4:**
	The following 3 interpreters of convergence in probability is equivalent:
	
*  $ X_n\stackrel{p}{\to}X $
*  $ \forall \epsilon>0,\exists N\in\mathbb{N}_+,\forall n\geq N,\forall\delta>0, Pr\{|X_n-X|>\delta\}< \epsilon $.
*  $ \forall \epsilon>0,\exists N\in\mathbb{N}_+,\forall n\geq N, Pr\{|X_n-X|>\epsilon\}< \epsilon $.
	
\#

**Proof:**
$ 1\iff 2 $ by the definition of limitation, $ 2\to 3 $ by letting $ \delta=\epsilon $. We prove $ 3\to 2 $. To prove 2 holds $ \forall\delta>0 $, we have the following 3 cases:
	
*  $ \delta=\epsilon $. From 3 we get 2 immediately.
*  $ \delta<\epsilon $. As $ \delta>0 $, by 3 $ \exists N\in\mathbb{N}_+,\forall n\geq N, Pr\{|X_n-X|>\delta\}< \delta<\epsilon $.
*  $ \delta>\epsilon $. Then $ \exists N\in\mathbb{N}_+,\forall n\geq N, Pr\{|X_n-X|>\delta\}<Pr\{|X_n-X|>\epsilon\}<\epsilon $.
	
So $ 2\iff 3 $.
\#
 

**Definition 4:**
	(Convergence Almost Everywhere):\\
	A sequence $ X_1,X_2,\cdots $ of RVs is said to converge almost everywhere, or converges with probability 1 to a RV $ X $, denoted $ X_n\stackrel{a.s.}{\to}X $ iff 

$$
\begin{align}

	Pr\{\lim\limits_{n\to\infty}X_n=X\}=1
	\end{align}
$$

or equivalently,
	

$$
\begin{align}

		 P\left(\{\omega\in\Omega:\lim\limits_{n\to\infty}X_n(\omega)=X(\omega)\}\right)=1\\
		\forall \epsilon>0, P\left( \limsup_{n\to\infty}\{\omega\in\Omega:|X_n(\omega)-X(\omega)|>\epsilon \}  \right)=0
	\end{align}
$$

\#


**Definition 5:**
	(Convergence Everywhere):\\
	A sequence $ X_1,X_2,\cdots $ of RVs is said to converge everywhere, or converges pointwosely to a RV $ X $, denoted $ X_n\to X $ iff 

$$
\begin{align}

	\lim\limits_{n\to\infty}X_n=X
	\end{align}
$$

or equivalently,
	

$$
\begin{align}

	\{\omega\in\Omega:\lim\limits_{n\to\infty}X_n(\omega)=X(\omega)\}=\Omega
	\end{align}
$$

\#


**Definition 6:**
	(Convergence in Mean):\\
	Let $ r\geq 1 $, a sequence $ X_1,X_2,\cdots $ of RVs is said to converge in the $ r $-th mean, or in the $ L^r $-norm to a RV $ X $, denoted $ X_n\stackrel{L^r}{\to} X $ iff the $ r $-th absolute moments $ E[|X_n|^r] $, and $ E[|X|^r] $ exists, and 

$$
\begin{align}

	\lim\limits_{n\to\infty}E[|X_n-X|^r]=0
	\end{align}
$$

\#


**Lemma 5:**
	(implimentations of RV convergences):\\
	The relations between the above 4 kinds of convergences are shown as follows:
	
*  Convergence in probability implies convergence in distribution, but convergence in distribution implies convergence in probability when the limiting random variable X is a constant.
*  Almost sure convergence implies convergence in probability, but convergence in probability does not imply almost sure convergence.
*  By Markov's inequality $ Pr\{X\geq a\}\leq \frac{E[X]}{a} $, convergence in the $ r $-th mean, for $ r \geq 1 $, implies convergence in probability.
*  if $ r > s \geq 1 $, convergence in $ r $-th mean implies convergence in $ s $-th mean.
*  Sure convergence of a random variable implies all the other kinds of convergence stated above.
	
\#

## Law of Large Numbers
We review the definition of LLN, performance of large times of experiments that the average tends to the expected value (when it exists).* Note: The average of trials may not converge in some cases because of heavy tails, such as Cauchy distribution (where it has no expectation) and Pareto distribution when $ \alpha<1 $ (where it has infinite expectation). We mainly talk about i.i.d. Lebesgue integrable RV sequence $ 
	\{X_k\}_{k\in\mathbb{N}} $ generated by $ X $, where $ E[X]=\mu $, $ Var(X)=\sigma^2 $
* Note: Lebesgue integrability of $ X_k $ means that the expected value $ E[X_k] $ exists according to Lebesgue integration and is finite. It does not mean that the associated probability measure is absolutely continuous w.r.t. Lebesgue measure.


**Theorem 1:**
	(Khinchin's weak LLN): The sample average converges in probability towards the expected value
	

$$
\begin{align}

	\bar{X}_n\stackrel{p}{\to}\mu,\quad n\to\infty
\end{align}
$$
 
\#

Actually, finite variance is not necessary though it may simplify the related proof. Large or infinite variance may make the convergence slower but LLN also holds. The convergence of $ \bar{X} $ to a degenerate RV requires $ Var(\bar{X})=\sigma^2/n $ to converge to 0, which may be true even if $ \sigma^2\to\infty $. In Chebyshev's weak LLN, we release the restriction of i.i.d. sequence and finite variance:


**Theorem 2:**
	(Chebyshev's weak LLN): For independent Lebesgue integrable RV sequence $ \{X_k\}_{k\in\mathbb{N}} $ with equal expected value $ \mu $, if $ \lim_{n\to\infty}Var(\bar{X}_n)=0 $, then:
	

$$
\begin{align}

	\bar{X}_n\stackrel{p}{\to}\mu,\quad n\to\infty
	\end{align}
$$
 
\#
Reminds: weak LLN may hold when the expectation do not exist.


**Example 2:**
	Let $ \{X_k\}_{k\in\mathbb{N}} $ be an independent zero-mean Gaussian RV sequence with $ Var(X_k)=\frac{2n}{\log (n+1)} $, which is not bounded. 
	

$$
\begin{align}

	Var(\bar{X})=Var(\frac{1}{n}\sum_{i=1}^nX_i)=\frac{1}{n^2}Var(\sum_{i=1}^nX_i)=\frac{1}{n^2}\sum_{i=1}^nVar(X_i)=\frac{1}{\log n}\to 0
\end{align}
$$

which satisfies the weak LLN.
\#


**Theorem 3:**
	(Kolmogorov's strong LLN):
	
*  $ \bar{X}_n\stackrel{a.s.}{\to}\mu,\quad n\to\infty $
*  when $ \{X_k\}_{k\in\mathbb{N}} $ are not i.i.d, then $ \bar{X}_n-E[\bar{X}_n]\stackrel{a.s.}{\to} $, provided that $ \sum_{k=1}^{\infty} \frac{1}{k^2}Var(X_k)<\infty $ and $ \forall k\in\mathbb{N}, X_k $ has finite second moment.
	 
\#
* Note: The strong Law is seen to be a special case of the pointwise ergodic theorem
* Note: The strong LLN can derive the weak one but do not hold in cases when the expected value do not exist.

The differences between the weak law and the strong law are in that:

*  The weak law states that for a specified large  n , the average  $ \bar{X}_{n} $  is likely to be near  $ \mu $ . Thus, it leaves open the possibility that  $ \left|\bar{X}_{n}-\mu\right|>\epsilon $  happens an infinite number of times, although at infrequent intervals. (Not necessarily  $ \left|\bar{X}_{n}-\mu\right| \neq 0 $  for all $ n $).
*  The strong law shows that this almost surely will not occur. In particular, it implies that with probability 1, we have that for any  $ \epsilon>0 $  the inequality  $ \left|\bar{X}_{n}-\mu\right|<\epsilon $  holds for all large enough  $ n $ .

	 
The strong law does not hold in the following cases, but the weak law does.

**Example 3:**
	
*  Let  $ X $  be an exponentially distributed random variable with parameter 1 . The random variable  $ \sin X e^{X} X^{-1} $  has no expected value according to Lebesgue integration, but using conditional convergence and interpreting the integral as a Dirichlet integral, which is an improper Riemann integral, we can say:


$$
\begin{align}

	E\left(\frac{\sin (X) e^{X}}{X}\right)=\int_{0}^{\infty} \frac{\sin (x) e^{x}}{x} e^{-x} d x=\frac{\pi}{2}
\end{align}
$$

*  Let  $ x $  be geometric distribution with probability  $ p=1/2 $ . The random variable  $ 2^{X}(-1)^{X} X^{-1} $  does not have an expected value in the conventional sense because the infinite series is not absolutely convergent, but using conditional convergence, we can say:


$$
\begin{align}

	E\left(\frac{2^{X}(-1)^{X}}{X}\right)=\sum_{1}^{\infty} \frac{2^{x}(-1)^{x}}{x} 2^{-x}=-\ln (2)
\end{align}
$$

*  If the cumulative distribution function of a random variable is


$$
\begin{align}

	\begin{array}{l}
1-F(x)=\frac{e}{2 x \ln (x)}, x \geq e \\
F(x)=\frac{e}{-2 x \ln (-x)}, x \leq-e
\end{array}
\end{align}
$$

then it has no expected value, but the weak law is true.
	
\# 
For sequence of i.i.d. functions of RV: $ \{f(X_k,\theta)\}_{k\in \mathbb{N}} $ with parameter $ \theta\in\Theta $, by the strong LLN we know that for fixed $ \theta $, the sample mean converges to $ E[f(X,\theta)] $. This is known as the pointwise convergence in $\theta$.  To make the convergence happens uniformly in $ \theta $, we have the **Uniform** LLN.


**Theorem 4:**
	(Uniform LNN): For i.i.d. functions of RV: $ \{f(X_k,\theta)\}_{k\in \mathbb{N}} $ with parameter $ \theta\in\Theta $ where $ E[f(X,\theta)] $ exists for all $ \theta $, if :
	
*   $ \Theta $  is compact
*  $ f(x, \theta) $  is continuous at each  $ \theta \in \Theta $  for almost all  $ x\in\mathcal{X} $ , and measurable function of  $ x $  at each  $ \theta $ 
*  there exists a dominating function  $ d(x) $  such that  $ E[d(X)]<\infty $ , and

$$
\begin{align}

	\|f(x, \theta)\| \leq d(x) \quad \text { for all } \theta \in \Theta
\end{align}
$$

	
Then  $ E[f(X, \theta)] $  is continuous in  $ \theta $ , and


$$
\begin{align}

	\sup _{\theta \in \Theta}\left\|\frac{1}{n} \sum_{i=1}^{n} f\left(X_{i}, \theta\right)-\mathrm{E}[f(X, \theta)]\right\| \stackrel{\mathrm{a.s.}}{\longrightarrow} 0
\end{align}
$$

\#
This result is useful to derive consistency of a large class of estimators known as Extremum estimator.

Moreover, an intuitive notion of probability as a long-run relative frequency leads us to the Borel LNN:

**Theorem 5:**(Borel LLN):
	If an experiment $ (\Omega,\mathcal{B},\mathbf{P}) $ is repeated a large number of times independently and under identical conditions, then 
	

$$
\begin{align}

	n\to\infty, \frac{N_n(A)}{n}\stackrel{a.s.}{\to}P(A),\quad \forall A\in\mathcal{B}
\end{align}
$$

\#


**Lemma 6:**
	(Chebyshev's Inequality):
	

$$
\begin{align}

	Pr\{|X-E[X]\geq k\sigma\}\leq \frac{1}{k^2},\quad \forall k>0, \sigma^2=Var(X).
\end{align}
$$

\#


**Lemma 7:**
	(Markov's Inequality): Let $ X $ be a non-negative RV, then
	

$$
\begin{align}

	Pr\{X\geq a\}\leq \frac{E[X]}{a}
\end{align}
$$

\#

An intuition to Markov's Inequality is that $ E[X]=Pr\{X<a\}E[X|X<a]+Pr\{X\geq a\}E[X|X\geq a] $. So when $ E[X|X<a]\geq 0 $ where $ X>0 $, for any possible distribution $ p_X $, the value $ E[X|X\geq a]\geq a $. Thus $ E[X]\geq Pr\{X\geq a\}E[X|X\geq a]\geq Pr\{X\geq a\}a $.

## Weak AEP
### Proof of Weak AEP

**Theorem 6:**
	(Weak AEP 1):
	

$$
\begin{align}

	n\to\infty,\quad -\frac{1}{n}p(X^n)\stackrel{p}{\to} H(X)
\end{align}
$$

or equivalently, let $ \mathcal{W}_{[X]{\epsilon}}^n\stackrel{\Delta}{=}\{x^n\in \mathcal{X}^n: |-\frac{\log p(x^n)}{n}-H(X)|\leq \epsilon\} $, then

*  $ \forall x^n\in \mathcal{W}_{[X]\epsilon}^n,\quad 2^{-n(H(X)+\epsilon)}\leq p_(x)\leq 2^{-n(H(X)-\epsilon)}$;
*  $ \forall \epsilon>0,\exists N\in\mathbb{N}_+,\forall n>N, Pr\{X^n\in \mathcal{W}_{[X]\epsilon}^n\}>1-\epsilon $.
*  $ \forall \epsilon>0,\exists N\in\mathbb{N}_+,\forall n>N, (1-\epsilon)2^{n(H(X)-\epsilon)}\leq |\mathcal{W}_{[X]\epsilon}^n|\leq 2^{n(H(X)+\epsilon)}.$

We call the set $ \mathcal{W}_{[X]\epsilon}^n $ the weekly typical set, $ x^n\in \mathcal{W}_{[X]\epsilon}^n $ the weakly typical sequence, and $ -\frac{\log p(x^n)}{n} $ the empirical entropy of sequence $ x^n $.
\#

**Proof:**
	By the week law of large numbers of i.i.d. sources, $ n\to\infty, -\frac{1}{n}\log p(X^n)=-\frac{1}{n}\sum_{i=1}^{n}\log p(X_i)\stackrel{p}{\to}-E[\log p(X)]=H(X) $.
\#

The weak AEP shows that a small set (compared to $ \mathcal{X}^n$, $ \mathcal{W}_{[X]\epsilon}^n $ is exponentially small) contains almost all probability of $ \mathcal{X}^n $ with nearly uniform distribution. So randomly choose a sequence from $ \mathcal{X}^n$, the probability are near $ \frac{1}{|\mathcal{W}_{[X]\epsilon}^n|} $ with high probability.* Note: The weekly typical sequence is different from the most likely sequence. It is not necessary fora a weakly typical set to include most likely sequences to possess the probability 1.

### Extension of weak AEP: Shannon-McMillan-Breiman(SMB) Theorem

**Theorem 7:**
	(Cramer theorem):\\
	Let $ \{X_k\}_{k\in\mathbb{N}} $ be a sequence of i.i.d. RVs with finite logarithmic moment generating functuion $ \Lambda(t)=\log E[e^{tX}]<\infty $, then the Legendre transform of $ \Lambda $ satisfies:
	

$$
\begin{align}

	\lim\limits_{n\to\infty}\frac{-\log(Pr\{\sum_{k=1}^{n}X_k\geq nx\})}{n}=\Lambda^*(x)\stackrel{\Delta}{=}\sup_{t\in\mathbb{R}}(tx-\Lambda(t))
\end{align}
$$

\#
* Note: This intuitively states that the probability of a large deviation from mean decays exponentially with number of samples $ n $.


**Theorem 8:**
	(SMB Theorem):\\
	Let $ \{X_n\} $ be a stationary ergodic process defined on a probability space $ (\Omega,\mathcal{B}, \mathbf{P}) $, then the weak AEP for $ \{X_n\} $ shows that 
	

$$
\begin{align}

	n\to\infty,\quad -\frac{1}{n}\log p(X^n)\stackrel{a.e.}{\to}H
	\end{align}
$$

where $ H $ is the entropy rate.
\#

The assumptions of stationarity/ergodicity/identical of RV is not necessary for the AEP to hold. An intuitive idea is that a form that LLN holds may be applied to weak AEP.

**Theorem 9:**
	For independent source $ \{X_k\}_{k\in\mathbb{N}} $ with bounded $ Var(\log p(X_i)) $, then the weak AEP holds:
	

$$
\begin{align}

	n\to\infty,\quad -\frac{1}{n}\log p(X^n)\stackrel{p}{\to}\bar{H}(X)\stackrel{\Delta}{=}\frac{1}{n}H(X_1,\cdots, X_n)
\end{align}
$$

\#

## Strong AEP and method of type
We introduce a new kind of AEP, which is related to Borel's LLN. The following relations are **called the method of types**, as the term **type** is given as an equivalence relation and the probability of the equivalence class gives the definition of typical set and the corresponding strong AEP:
### Cross Entropy and type

**Definition 7:**
	(Empirical Distribution):\\
	For a given random sequence $x^n\in \mathcal{X}^n$, The number of appearances of $a$  in the sequence:
	

$$
\begin{align}

	N(a|x^n)=\sum_{k=1}^{n}\delta_{x_i,a},\quad \forall a\in \mathcal{X}
	\end{align}
$$

where $\delta_{a,b}$ is the Kronecker symbol and returns $1$ ony if $a=b$.  We denote:
	

$$
\begin{align}

	Q(a)=P_{x^n}(a)=\frac{1}{n}N(a|x^n), 
	\end{align}
$$
<a id="Empirical">2</a>

as the empirical distribution of any given $x^n$, and from ([here](Empirical)), empirical distribution $Q$ can also be seen as the frequency  $P_{x^n}$.
\#

For i.i.d. sequence $X^n$ with distribution $p_X$, and empirical distribution $P_{x^n}$ in a specific $x^n\in\mathcal{X}^n$, we calculate the $Pr(X^n=x^n)$.


$$
\begin{align}

&\frac{1}{n}logPr(X^n=x^n)\\
=&\frac{1}{n}log\prod_{i=1}^{n}P_X(x_i)\\
=&\frac{1}{n}log\prod_{a\in\mathcal{X}}P_X(a)^{N(a|x^n)}\\
=&\sum_{a\in\mathcal{X}}\frac{N(a|x^n)}{n}logP_X(a)\\
=&\sum_{a\in\mathcal{X}}Q(a)logP_X(a)<a id="Cross Entropy">3</a>
\end{align}
$$


This indicates that the probability of a random sequence only depends on the distribution of each random variable $X$ and the frequency of the value $x^n$. Like the definition of emprical entropy in the weak AEP, we define the cross entropy:

**Definition 8:**
	(Cross Entropy):\\
	We define the cross entropy in an i.i.d. trial with $ n $ implements of RV $ X $ as:
	

$$
\begin{align}

	H(Q,P_X)=-\sum_{a\in\mathcal{X}}Q(a)logP_X(a), <a id="Def Cross Entropy">4</a>
	\end{align}
$$

\#

From the definition ([here](#Def Cross Entropy)),


$$
\begin{align}

Pr(X^n=x^n)=q^{-nH(Q,P_X)}
\end{align}
$$


Easy to see that if all the frequency of  $a\in\mathcal{X}$ on different $x^n$s are the same, the values of probability distribution of $X^n$ on point $x^n$s are the same. This allows us to divide the sample space $\mathcal{X}^n$ into different parts and each part has the same empirical distribution, and in each part, sequences are automatically uniformly distributed. The partition is done only by $Q:\mathcal{X}\to \frac{[n]}{n}$. For a formal definition,

**Definition 9:**
	(type):\\
	For an i.i.d. trial of $ n $ complements of RV $ X $ over a finite alphabet $ \mathcal{X} $, the type w.r.t. emperical distribution $ Q $ is defined by:
	

$$
\begin{align}

	\mathcal{T}_Q^n=\{x^n\in X^n|P_{x^n}=Q\}
	\end{align}
$$

so any type $\mathcal{T}_Q^n \subseteq \mathcal{X}^n$ is a set of sequences whose probability are numberially the same.
\#
By combinatorial theory, the number of types is the munber of possible empirical distributions:



$$
\begin{align}

\binom{n+|\mathcal{X}|-1}{n}\leq (n+1)^{|\mathcal{X}|}
\end{align}
$$


which is a ploynomial of n* Note: The question of the number of types is equivalent to the question, in which n different balls are independently labeled with $ |\mathcal{X}| $ labels, or we choose n unordered balls from an urn containing $|\mathcal{X}|$ balls with replacement.}


**Definition 10:**
	(Rate of a Quantity):\\
	For any quantity $ M $ which is exponentially large or exponentially small, we call the $ \frac{1}{n}\log M $ the rate of $ M $, where the $ \log $ takes base of a convenient integer.
\#


### Size of a Type

**Lemma 8:**
	(Size of a Type):\\
	For $n$ i.i.d. experiments over the implement of $X\in\mathcal{X}$, the size of any type satisfies:
	

$$
\begin{align}

		\frac{1}{n}log|\mathcal{T}_Q^n|\sim H(Q,Q)=H(Q),\quad n\to \infty
	\end{align}
$$

As the size of type only depends on the empirical distribution $Q=P_{x^n}$, this theorem introduces a natural constant for any given distribution $Q$:


$$
\begin{align}

H(Q)=H(Q,Q)=-\sum_{a\in\mathcal{X}}Q(a)logQ(a)
\end{align}
$$

which can be an alternative definition of entropy.
\#

**Proof:**
	 The size of any type can be shown combinatorially:


$$
\begin{align}

|\mathcal{T}_Q^n|=\frac{n!}{\prod_{a\in\mathcal{X}}[nQ(a)]!}
\end{align}
$$

and noticing the Stirling approximation: 


$$
\begin{align}

n^n\sim n!e^n\to \frac{1}{n}lnn!\sim ln n-1,\quad n\to \infty
\end{align}
$$

We have:


$$
\begin{align}

&\frac{1}{n}log|\mathcal{T}_Q^n|\\
\sim &(lnn-1)-\sum_{a\in \mathcal{X}}Q(a)(ln[nQ(a)]-1)\\
=&(lnn-1)-(lnn-1)\sum_{a\in\mathcal{X}}Q(a)-\sum_{a\in\mathcal{X}}Q(a)logQ(a)\\
=&-\sum_{a\in\mathcal{X}}Q(a)logQ(a)=H(Q,Q), \quad n\to \infty <a id="entr">5</a>
\end{align}
$$

\#

It is worth noticing that $\frac{1}{n}log|\mathcal{T}_Q^n|\sim H(Q)$ is a exponential approximation, which allows an deviation of a ploynomial times of the size.* Note: This is true that for any ploynomial $ P(x)\in \mathbb{R[x]} $, $\lim\limits_{n\to \infty}\dfrac{e^x}{P(x)}=0$}.
Specifically, for $\mathcal{T}_Q^n$ with $Q$ happens to be the distribution of $X$, i.e., $Q=P_X$, 


$$
\begin{align}

\frac{1}{\binom{n+|\mathcal{X}|-1}{n}} \leq \sum_{x^n\in\mathcal{T}_Q^n}\prod_{i=1}^{n}p_{X}(x_i)=Q^n(\mathcal{T}_Q^n)\leq 1
\end{align}
$$


and by $[here](Def Cross Entropy)$, $\forall x^n\in \mathcal{T}_Q^n, P_{X^n}(x^n)=Q^n(x^n)=q^{-nH(Q)}$. So, we get the two-side bounds of the size of types: * Note: In fact we can choose any possible $ P_X $ as the number of types are independent with $ p_X $.  We choose $ P_X=Q $ to get a proper lower bound, as the probability will be maximum when $ p_X=Q $


$$
\begin{align}

\frac{q^{nH(Q)}}{\binom{n+|\mathcal{X}|-1}{n}} \leq |\mathcal{T}_Q^n|\leq q^{nH(Q)}, <a id="specsize">6</a>
\end{align}
$$


### Probability of a type

**Lemma 9:**
(Probability of a type):\\ For $ n $ i.i.d. implements of RV $ X\sim p $, when $ n\to\infty $, 
	

$$
\begin{align}

	\frac{1}{n}\log p_{X^n}(\mathcal{T}_Q^n)\sim D(Q||p)
	\end{align}
$$

As the probability of type depends on the empirical distribution $Q=P_{x^n}$ and real distribution $ p $, this theorem introduces a natural constant for any given distribution $Q$ and $ p $:
	

$$
\begin{align}

	H(Q,p)-H(Q)=D(Q||p)=-\sum_{a\in\mathcal{X}}p(a)log\frac{p(a)}{Q(a)}=D(Q||p)\geq 0
	\end{align}
$$

which can be an alternative definition of Kullback-Liebler Divergence (or relative entropy).
\#

**Proof:**
We can simply calculate the probability of any given type $\mathcal{T}_Q^n$ by the multiplication of the probability of any point in the type(as thay are uniformly distributed) and the size of the type, which is given in ([here](#Def Cross Entropy)) and ([here](#entr)):
	

$$
\begin{align}

	&\frac{1}{n}\log P_{X^n}(\mathcal{T}_Q^n)\\
	=&\frac{1}{n}\log[|\mathcal{T}_Q^n|P_{X^n}(x^n:x^n\in \mathcal{T}_Q^n)]\\
	\sim &\frac{1}{n}\log|\mathcal{T}_Q^n|+\frac{1}{n}logP_{X^n}(x^n:P_{x^n}=Q)\\
	=&H(Q)-H(Q,p), 
	\end{align}
$$

<a id="relativeentr">7</a>

To put it more specifically from  ([here](#specsize)),


$$
\begin{align}

\frac{q^{-nD(Q||p)}}{\binom{n+|\mathcal{X}|-1}{n}}\leq P_{X^n}(\mathcal{T}_Q^n)=|\mathcal{T}_Q^n|P_{X^n}(x^n:x^n\in \mathcal{T}_Q^n)\leq q^{-nD(Q||p)}
\end{align}
$$

\#

([here](relativeentr)) shows that the difference between $H(Q)$ and $H(Q,P_X)$ (i.e., the difference of empirical distribution and real distribution) determines the probability of a certain type. (Compared to the size of a type, which is only determined by the empirical distribution). We can intuitively cosnsider $D(Q||P_X)$ as the "distance" between 2 distributions. The large the distance of $Q$ and $P_X$ is, the less $P_{X^n}(\mathcal{T}_Q^n)$ will be. As a specific case when $P=Q$, $D(Q||P_X)=0$ and the probability gets maximum.

### Strong AEP
Although it seems that when $P=Q$ , $\frac{1}{n}logP_{X^n}(\mathcal{T}_Q^n)\sim 0$, however, $P_{X^n}(\mathcal{T}_Q^n)\sim1\\$ is not correct as the former approximation is in a exponential sense. In fact, when  $n\to \infty$  , the number of types "near" $P_X$, say, $\exists a\in \mathcal{X}, |Q(a)-P_X(a)|\leq \delta$ , is no less than $[2n\delta]$  with nearly (the difference will be bounded in the following statement) the same probability, so the probability of type $ P_{X^n}(\mathcal{T}_{P_X}^n)\sim 1/2n\delta\to 0, \quad n\to \infty$. So we  do not care any possibility of any *certain type* but a  *range of types*. In this section we show that the possibility concentrates exactly around the maximum type $\mathcal{T}_{P_X}^n$. 

* Note: If only $ a\in \mathcal{X} $ changes, $ Q(a)=\dfrac{N(a|x^n)}{n}\to N(a|x^n)=nQ(a)\in [ n(P_X(a)-\delta),  n(P_X(a)+\delta) ] $, so basically there are no less than $ [2n\delta] $ different $ N(a|x^n) $, and thus $ [2n\delta] $ different types. }


**Definition 11:**
	(Strongly Typical Set):
	Let $ X\sim p $ be a RV defined on a finite alphabet $ \mathcal{X} $. We define the the union of all "near maximum" types as the *Strongly Typical Set*:
	

$$
\begin{align}

	\mathcal{T}_{[X]_\delta}^n=&\{x^n\in\mathcal{X}^n:||Q(a)-p_{X}(a)|\leq\delta,\forall a\in \mathcal{S}_X\wedge Q(a)=0,\forall a\notin \mathcal{S}_X\}\\
	=&\bigcup_{Q:|Q(a)-P_X(a)|\leq\delta,\forall a\in \mathcal{X},\wedge Q(a)=0,\forall a\notin \mathcal{S}_X}\mathcal{T}_Q^n
	\end{align}
$$

or alternatively,
	

$$
\begin{align}

	T_{[X]_{\delta^\prime}}^n=&\{x^n\in\mathcal{X}^n: \forall a\notin \mathcal{S}_X, Q(a)=0\wedge \sum_{x\in\mathcal{X}}||Q(x)-p(x)|\leq\delta^\prime\}
	\end{align}
$$

by letting $ \delta'=\sqrt{|\mathcal{X}|}\delta $. The completement of strongly typical set is called the strongly atypical set, denoted by $ \mathcal{T}_{[X]_\delta}^{nC}=\mathcal{X}^n-\mathcal{T}_{[X]_\delta}^n $ ($ T_{[X]_\delta}^{nC}=\mathcal{X}^n-T_{[X]_\delta}^n $ resp.). For $ x^n\in\mathcal{X}^n $, if $ \exists x_i\in \mathcal{X}, |Q(x_i)-p(x_i)|\geq\delta $, then $ x^n\in\mathcal{T}_{[X]_\delta}^{nC} $.
\#

The strong AEP are acknowledged with 3 lemmas, analogous to the weak AEP:

**Theorem 10:**
	(Strong AEP I: Size of Strongly Typical Set):
	

$$
\begin{align}

	\frac{1}{n}|\mathcal{T}_{[X]_\delta}^n|\sim H(p),\quad n\to\infty
	\end{align}
$$

\#
* Note: From [here](#entr we know that the size of type has a $ H(p) $ exponential approximation. However, The gap between them tends to be infinite, as the probability are tend to 1 and 0 from the following relation.) 


**Proof:** First we give a lemma according to the continuity of $ H(\cdot) $:
	
**Lemma 10:**
due to the uniform continuity of entropy function 
		

$$
\begin{align}

		H:\{(q_1,\cdots,q_{|\mathcal{X}|})|\forall i\in[n], q_i\in [0,1],\sum_{i=1}^{|\mathcal{X}|}q_i=1\}\to\mathbb{R}_+, H(Q)=-\sum_{a\in\mathcal{X}}Q(a)logQ(a)
		\end{align}
$$

we can find $\delta_{\epsilon}$ to make $|H(Q)-H(p)|\leq \epsilon$, i,.e.,
		

$$
\begin{align}

		\forall \epsilon >0, \exists \delta_\epsilon>0,|(q_1,\cdots,q_{|\mathcal{X}|})-(p_1,\cdots,p_{|\mathcal{X}|})|\leq \delta_1\to |H(Q)-H(p)|\leq \epsilon
		\end{align}
$$

\#
	
We pick* Note: Attention that we pick $ \delta $ from $ \epsilon $ but not $ \epsilon $ from $ \delta $. This $ \delta $ has a linear form of $ \epsilon $, so they have the same convergence when $ n\to\infty $.
	

$$
\begin{align}

	\delta_{\epsilon}=min\{\frac{\epsilon}{-\sum_{a\in \mathcal{X}}logp(a)},\frac{\epsilon}{-\sum_{a\in \mathcal{X}}logQ(a)}\}
	\end{align}
$$

and $H(Q)$ is bounded by:
	

$$
\begin{align}

	H(Q)\leq  &H(Q,P_X)=-\sum_{a\in\mathcal{X}}Q(a)logP_X(a)\\
	\leq  &-\sum_{a\in\mathcal{X}}(P_X(a)+\delta_\epsilon)logP_X(a)\\
	\leq &-\delta_\epsilon\sum_{a\in\mathcal{X}}logP_X(a)-\sum_{a\in\mathcal{X}}P_X(a)logP_X(a)\\
	=&\epsilon+H(P_X)
	\end{align}
$$

	

$$
\begin{align}

	H(Q)=&-\sum_{a\in\mathcal{X}}Q(a)logQ(a)\\
	\geq  &-\sum_{a\in\mathcal{X}}(P_X(a)-\delta_\epsilon)logQ(a)\\
	\geq & H(P_X)-\epsilon\frac{\sum_{a\in\mathcal{X}}logQ(a)}{\sum_{a\in\mathcal{X}}logQ(a)}\\
	=&H(P_X)-\epsilon
	\end{align}
$$

	

$$
\begin{align}

	|Q(a)-P_{X}(a)|\leq &\delta_{\epsilon},\forall a\in \mathcal{X}\to |H(Q)-H(P_X)|\leq \epsilon
	\end{align}
$$

Which ends the proof of lemma. We then calculate the upper bound of the size of typical set:
	

$$
\begin{align}

	&\frac{1}{n}log|\mathcal{T}_{[Q]_{\delta_\epsilon}}^n|\\
	=&\frac{1}{n}log\sum_{Q:|Q(a)-P_X(a)|\leq\delta,\forall a\in \mathcal{X}}|\mathcal{T}_Q^n|\\ 
	\leq & \frac{1}{n}log\binom{n+|\mathcal{X}|-1}{n}+\max_{Q:|Q(a)-P_X(a)|\leq\delta,\forall a\in \mathcal{X}}\frac{1}{n}log|\mathcal{T}_{Q}^n|\\
	= &H(Q)\leq H(P_X)+\epsilon, \quad n\to\infty
	\end{align}
$$

and the lower bound can be done by the same way:
	

$$
\begin{align}

	&\frac{1}{n}log|\mathcal{T}_{[Q]_{\delta_\epsilon}}^n|\\
	=&\frac{1}{n}log\sum_{Q:|Q(a)-P_X(a)|\leq\delta_\epsilon,\forall a\in \mathcal{X}}|\mathcal{T}_Q^n|\\ 
	\geq  &\min_{Q:|Q(a)-P_X(a)|\leq\delta_\epsilon,\forall a\in \mathcal{X}}\frac{1}{n}log|\mathcal{T}_{Q}^n|\\
	= &H(Q)\geq H(P_X)-\epsilon, \quad n\to\infty
	\end{align}
$$

\#


**Theorem 11:**
(Strong AEP II: Probability of Strongly Typical Set):
	

$$
\begin{align}

	\frac{1}{n}\log Pr\{X^n\in \mathcal{T}^{nC}_{[X]_{\delta_\epsilon}}\}\leq -\delta_\epsilon
	\end{align}
$$

As $ \lim_{n\to\infty}\delta_\epsilon=0 $, the probability of Strongly typical set tends to 1.
\#

**Proof:**
for all types $\mathcal{T}_Q^n\subseteq \mathcal{T}_{[Q]_{\delta_{\epsilon}}}^{nC}$  , $\exists a \in \mathcal{X}, |Q(a)-P_X(a)|\geq \delta_{\epsilon}$. Due to the continuity and monotony of $f(p)=logp$, we have:
	
* Note: ([here](taylor) follows from the definition of derivatives, and is not accurate. In fact, $ (logP_X(a)-logQ(a))= \frac{d(logp)}{dp}|_{p=Q(a)}[P_X(a)-Q(a)]+o((P_X(a)-Q(a))^2)$ is the Taylor formula with Peano remainder and the results should be $ \delta_\epsilon + Q(a)o(\delta^2) $. Here we omit the $ o(\delta^2) $, and we will configure $ \delta $ in ([here](make)) to make $ \lim\limits_{n\to \infty}nQ(a)o(\delta^2)\neq \infty $}
	

$$
\begin{align}

	&D(Q||p)=|H(p,Q)-H(Q)|\\
	=& |\sum_{a\in \mathcal{X}}Q(a)(\log p(a)-\log Q(a))|\\
	\geq  &Q(a)|\log p(a)-\log Q(a)|\\
	=&Q(a)\frac{d(logp)}{dp}|_{p=Q(a)}|P_X(a)-Q(a)|<a id="taylor">8</a>\\
	\geq& Q(a)\frac{1}{Q(a)}\delta_\epsilon=\delta_\epsilon> 0
	\end{align}
$$

Then we give the upper bound of atypical set:
	

$$
\begin{align}

	&\frac{1}{n}logPr(X^n\in\mathcal{T}_{[Q]_{\delta_\epsilon}}^{nC})\\
	=&\frac{1}{n}log\sum_{Q:\exists a\in \mathcal{X}, |Q(a)-p(a)|\geq\delta_\epsilon}|\mathcal{T}_Q^n|\\
	\leq  & \frac{1}{n}log\binom{n+|\mathcal{X}|-1}{n}+\max_{Q:|Q(a)-p(a)|\leq\delta,\forall a\in \mathcal{X}}\frac{1}{n}logPr(X^n\in\mathcal{T}_{Q}^{n})\\
	=&-D(Q||p)\leq -\delta_\epsilon, <a id="proaty">9</a>
	\end{align}
$$

\#

**Theorem 12:**
(Strong AEP III: The probability of Strongly Typical Sequence):
	

$$
\begin{align}

	\forall \delta>0,\exists \eta>0 s.t. -H(X)-\eta\leq\frac{1}{n}\log p(x^n)\leq -H(X)+\eta
	\end{align}
$$

\#

**Proof:** From AEP I and AEP II, we have
	

$$
\begin{align}

	-H(p)-\epsilon-\delta\leq \frac{1}{n}\log p(x^n)=-H(p,Q)=-H(Q)-D(Q||p)\leq -H(p)+\epsilon
	\end{align}
$$

and letting $ \eta=\delta+\epsilon $.
\#

One to be noticed is that in order to get a proper $\epsilon$ to make both $\epsilon$ itself and $ n\delta^2 $ be sufficiently small and $n\delta_{\epsilon}$ sufficiently large. For example, 


$$
\begin{align}

\epsilon=n^p , \quad  p\in(-1,-\dfrac{1}{2}], <a id="make">10</a>
\end{align}
$$

is a proper setting.

### Substantial Set

**Definition 12:**
	(Substantial Set):\\A set $\mathcal{A}\in \mathcal{X}^n$ is called a substantial set iff 
	

$$
\begin{align}

	Pr(X^n\in\mathcal{A})=\mu>0
	\end{align}
$$

\#

and intuitively, the positive probability can only be valued in the typical set when $n\to \infty$, as ([here](proaty)) shows that :


$$
\begin{align}

Pr(X^n\in\mathcal{T}_{[Q]_{\delta_\epsilon}}^{nC})\to 0,\quad n\to \infty
\end{align}
$$


To show this, we first calculate the probability of  intersection of $\mathcal{A}$ and typical set:



$$
\begin{align}

&Pr(X^n\in \mathcal{A}\cap \mathcal{T}_{[Q]_\delta}^n)\\
=&1-Pr(\overline{\mathcal{A}}\cup \mathcal{T}_{[Q]_{\delta_\epsilon}}^{nC})\\
\geq  &1-Pr(X^n\in \overline{\mathcal{A}})-Pr(X^n\in \mathcal{T}_{[Q]_{\delta_\epsilon}}^{nC})\\
\geq  &1-(1-\mu)-exp^{-n\delta_\epsilon}\to \mu,\quad n\to \infty
\end{align}
$$


so the probability almostly distributed in the typical set. We can calculate a lower bound of $\mathcal{A}$ by the property that the distribution in a typical set is uniform:



$$
\begin{align}

\frac{1}{n}log|\mathcal{A}|\geq  &\frac{1}{n}log|\mathcal{A}\cap \mathcal{T}_{[Q]_\delta}^n|\\
\geq  &\frac{1}{n}log(\mu-exp(-n\delta))+H(X)-\epsilon\\
\to & H(X)-\epsilon,\quad n\to \infty
\end{align}
$$

So any non-zero part of strongly typical set has the same exponential approximation as the strongly typical set itself.

## Stong typicality \& Weak typicality
The strong typicality is stronger in the sense that is can imply the weak typicality.

**Theorem 13:**
	$ \forall \delta>0, \exists \eta>0 $, s.t. $ \mathcal{T}_{[X]_\delta}^{n}\subseteq \mathcal{W}_{[X]_\eta}^{n} $
\#
The converse is not true. A counter example is that for $ X\sim p=(1/2,1/4,1/4) $, when $ x^n $ is a weakly typical sequence, then we need:


$$
\begin{align}

-\frac{1}{n}\log p(x)=-q(0)\log 1/2-q(1)\log 1/4 -q(2)\log 1/4\approx H(X)
\end{align}
$$

by letting $ q(0)=q(1)=0.5, q(2)=0 $, the sequence (without realization of $ p(2) $) is weekly typical, but apparently not strongly typical.

Stronger as the strong typicality is, it can only be used for RV under finite alphabets while the weak one corresponds to the weak LLN. Unless specified, we always use the term "typicality" to denote the strong typicality.

## Joint Typicality
Now we come into bivariate distribution scenario where 2 generic RVs $ X\in\mathcal{X},Y\in\mathcal{Y} $ are taken into consideration to produce the i.i.d. information source $ \{X_k,Y_k\}_{k\in\mathbb{N}} $.
### Properties of Jointly Typical Set

**Definition 13:**
	(Jointly typical set):\\ Let $ \{X_k,Y_k\}_{k\in\mathbb{N}} $ be an i.i.d. information source with 2 generic RVs $ X\in\mathcal{X},Y\in \mathcal{Y} $ under finite alphabets. The jointly typical set $ \mathcal{T}_{[XY]_\delta}^n $ is

$$
\begin{align}

	\mathcal{T}_{[XY]_\delta}^n=\{(x^n,y^n)&\in \mathcal{X}^n\times\mathcal{Y}^n: N(x,y;x^n,y^n)=0, \forall (x,y)\notin S_{X,Y}\wedge\\ &\left|\frac{N(x,y;x^n,y^n)}{n}-p(x,y)\right|\leq \delta,\forall (x,y)\in\mathcal{X}\times\mathcal{Y}\}\\
	T_{[XY]_\delta}^n=\{(x^n,y^n)&\in \mathcal{X}^n\times\mathcal{Y}^n: N(x,y;x^n,y^n)=0, \forall (x,y)\notin S_{X,Y}\wedge\\ &\sum_{x\in\mathcal{X}}\sum_{y\in\mathcal{Y}}\left|\frac{N(x,y;x^n,y^n)}{n}-p(x,y)\right|\leq \delta\}
	\end{align}
$$

$ \forall (x^n,y^n)\in\mathcal{T}_{[XY]_\delta}^n $ is called jointly typical.
\#

**Theorem 14:**(Properities of Jointly Typical Set):
		*  (Consistency): The jointly typical implies the typical separately:

$$
\begin{align}

		\forall \delta>0, \exists \delta_1,\delta_2>0, \lim\limits_{n\to\infty}(\delta,\delta_1,\delta_2)=0, s.t.\quad \mathcal{T}_{[XY]_\delta}\subseteq\mathcal{T}_{[X]_\delta}^n\times\mathcal{T}_{[Y]_\delta}^n
		\end{align}
$$

*  (Preservation): Let $ Y=f(X) $, then $ x^n=(x_1,\cdots,x_n)\in\mathcal{T}_{[X]_\delta}^n $ implies $ (f(x_1),\cdots,f(x_n))\in\mathcal{T}_{[Y]_\delta}^n $
	
\#

**Proof:**
The consistency of JT set can be proved by noticing $ N(x;x^n)=\sum_{y\in\mathcal{Y}}N(x,y;x^n,y^n) $
	

$$
\begin{align}

	\left|\frac{N(x;x^n)}{n}-p(x)\right|=\left|\sum_{y\in\mathcal{Y}}\left(\frac{N(x,y;x^n,y^n)}{n}-p(x,y)\right)\right|\leq |\mathcal{Y}|\delta=\delta_1
	\end{align}
$$

So $ \forall (x^n,y^n)\in\mathcal{T}_{[XY]_\delta}^n $, then $ x^n\in\mathcal{T}_{[X]_\delta}^n $. Similarly,$ \forall (x^n,y^n)\in\mathcal{T}_{[XY]_\delta}^n \to y^n\in\mathcal{T}_{[Y]_\delta}^n $.
	
For preservation, we notice that $ N(y, (f(x_1),\cdots,f(x_n)))=\sum_{x\in f^{-1}[y]}N(x;x^n) $.
	

$$
\begin{align}

	\left|\frac{N(y;y^n)}{n}-p(y)\right|=&\left|\sum_{x\in f^{-1}[y]}\frac{N(x;x^n)}{n}-p(x)\right|\\
	\leq& \sum_{x\in f^{-1}[y]}\left|\frac{N(x;x^n)}{n}-p(x)\right|\leq |f^{-1}[y]|\delta=\delta^\prime
	\end{align}
$$

Therefore, $ y^n=(f(x_1),\cdots,f(x_n))\in\mathcal{T}_{[Y]_{\delta^\prime}}^n $.
\#

### Joint AEP

**Definition 14:**
Let $ (X^n,Y^n)=((X_1,Y_1),\cdots,(X_n,Y_n)) $ be i.i.d. sequence with generic RV $ (X,Y) $, then there exists $ \epsilon,\eta>0 $ s.t. $ \epsilon,\eta\to 0 $ as $ \delta\to 0 $, and
	

$$
\begin{align}

		\forall (x^n,y^n)\in\mathcal{T}_{[XY]_\delta}^n,\quad -H(X,Y)-\epsilon\leq& \frac{1}{n}\log p(x^n,y^n)\leq -H(X,Y)+\epsilon\\
		&\frac{1}{n}\log Pr\{(X^n,Y^n)\in\mathcal{T}_{[XY]_\delta}^n\}\leq -\delta\\
		H(X,Y)-\eta\leq &\frac{1}{n}\log |\mathcal{T}_{[XY]_\delta}^n|\leq H(X,Y)+\eta
		\end{align}
$$

\#

**Proof:**
	The proof is similar to the proof of strong AEP, omitted.
\#

## Conditional Typicality
From the JAEP, we know that when $ n\to\infty $, $ \frac{1}{n}\log|\mathcal{T}_{[XY]_\delta}^n|\to H(X,Y) $ and $ \frac{1}{n}\log|\mathcal{T}_{[X]_\delta}^n|\to H(X) $, and that $ (X^n,Y^n) $ (resp. $ X^n $) is uniformly distributed in $ \mathcal{T}_{[XY]_\delta}^n $ (resp. $ \mathcal{T}_{[X]_\delta}^n $). Then for each $ x^n\in\mathcal{T}_{[X]_\delta}^n $, the number of typical sequence $ (x^n,y^n) $ are exponentially the same, each with $ \frac{1}{n}\log \frac{|\mathcal{T}_{[XY]_\delta}^n|}{|\mathcal{T}_{[X]_\delta}^n|}\to H(Y|X) $. Thus we can define the typicality of $ y^n $ conditioning on a given $ x^n\in \mathcal{T}_{[X]_\delta}^n $.

**Definition 15:**
	(Conditional Typical Set):\\
For any $ x^n\in\mathcal{T}_{[X]_\delta}^n $, the sequence $ y^n\in \mathcal{T}_{[Y]_\delta}^n $ which makes $ (x^n,y^n) $ jointly typical are called the typical sequence conditioning on $ x^n $, i.e.
	

$$
\begin{align}

	\mathcal{T}_{[Y|X]_\delta}^n(x^n)=\{y^n\in \mathcal{T}_{[Y]_\delta}^n: (x^n,y^n)\in\mathcal{T}_{[XY]_\delta}^n\}.
	\end{align}
$$

The $ \mathcal{T}_{[Y|X]_\delta}^n(x^n) $ is called the typical set of $ Y $ conditioning on $ x^n $.
\#


**Theorem 15:**
	(Conditional AEP):
	

$$
\begin{align}

	\forall x^n\in\mathcal{T}_{[X]_\delta}^n&\text{ s.t.}|\mathcal{T}_{[Y|X]_\delta}^n(x^n)|\geq 1, \exists \eta>0, \eta\to 0 \text{ as } \delta\to 0\text{ we have: }\\
	 &\quad H(Y|X)-\eta\leq |\mathcal{T}_{[Y|X]_\delta}^n(x^n)|\leq H(Y|X)+\eta
	\end{align}
$$

\#

**Proof:**
$ \forall x^n\in\mathcal{T}_{[X]_\delta}^n $, we have
	

$$
\begin{align}

	p(x^n)=&\sum_{y^n\in \mathcal{Y}^n}p(x^n,y^n)\\
	\geq& \sum_{y^n\in\mathcal{T}_{[Y|X]_\delta}^n(x^n)}p(x^n,y^n)=|\mathcal{T}_{[Y|X]_\delta}^n(x^n)|p(x^n,y^n), \quad\forall y^n\in\mathcal{T}_{[Y|X]_\delta}^n(x^n)
	\end{align}
$$

so the upper bound of the size can be derived by the bounds from JAEP and AEP:
	

$$
\begin{align}

	\frac{1}{n}\log|\mathcal{T}_{[Y|X]_\delta}^n(x^n)|\leq& \frac{1}{n}\log (p(x^n)-p(x^n,y^n))\\
	\leq& -H(X)+\eta_1-(-H(X,Y)-\eta_2)=H(Y|X)+\eta ,\quad  \eta=\eta_1+\eta_2
	\end{align}
$$

Actually, $\forall (x^n,y^n)\in\mathcal{T}_{[XY]_\delta}^n $ with emperical distribution $ K $, the size of the type with $ K $ is:
	

$$
\begin{align}

	|\mathcal{T}_{K}^n|=\frac{n!}{\prod_{(x,Y)\in \mathcal{X}\times\mathcal{Y}}(nK(x,y))!}=\frac{n!}{\prod_{(x,Y)\in \mathcal{X}\times\mathcal{Y}}N(x,y;x^n,y^n)!}
	\end{align}
$$

for fixed $ x^n\in \mathcal{T}_{[X]_\delta}^n $, the size reduces to:
	

$$
\begin{align}

	\prod_{x\in\mathcal{X}}\frac{N(x;x^n)!}{\prod_{y\in\mathcal{Y}}N(x,y;x^n,y^n)!}
	\end{align}
$$

which can be a lower bound of the $ |\mathcal{T}_{[XY]_\delta}^n(x^n)| $. i.e.,
	

$$
\begin{align}

	&\frac{1}{n}\log|\mathcal{T}_{[Y|X]_\delta}^n(x^n)|\\
	\geq& \frac{1}{n}\log \prod_{x\in\mathcal{X}}\frac{N(x;x^n)!}{\prod_{y\in\mathcal{Y}}N(x,y;x^n,y^n)!}\\
	\stackrel{a}{\geq}& \frac{1}{n}\sum_{x\in\mathcal{X}}\left(N(x;x^n)\log N(x;x^n)-N(x;x^n)\right)\\
	&-\frac{1}{n}\sum_{x\in\mathcal{X}}\sum_{y\in\mathcal{Y}}\left((N(x,y;x^n,y^n)+1)\log(N(x,y;x^n,y^n)+1)-N(x,y;x^n,y^n)\right)\\
	=&\frac{1}{n}\sum_{x\in\mathcal{X}}\left(N(x;x^n)\log N(x;x^n)-\sum_{y\in\mathcal{Y}}(N(x,y;x^n,y^n)+1)\log(N(x,y;x^n,y^n)+1)\right)\\
	\stackrel{b}{\geq}&\frac{1}{n}\sum_{x\in\mathcal{X}}\left(N(x;x^n)\log (n(p(x)-\delta))-\sum_{y\in\mathcal{Y}}(N(x,y;x^n,y^n)+1)\log(n(p(x,y)+\delta+\frac{1}{n}))\right)\\
	=& \sum_{x\in\mathcal{X}}\left(\frac{N(x;x^n)}{n}\log (p(x)-\delta)-\sum_{y\in\mathcal{Y}}(\frac{N(x,y;x^n,y^n)+1}{n})\log(p(x,y)+\delta+\frac{1}{n})\right)\\
	&+\frac{1}{n}\sum_{x\in\mathcal{X}}\left(N(x;x^n)-\sum_{y\in\mathcal{Y}}(N(x,y;x^n,y^n)+1)\right)\log n\\
	\stackrel{c}{\geq} & \sum_{x\in\mathcal{X}}\left((p(x)+\delta)\log (p(x)-\delta)-\sum_{y\in\mathcal{Y}}(p(x,y)-\delta+\frac{1}{n})\log(p(x,y)+\delta+\frac{1}{n})\right)-\frac{\log n}{n}|\mathcal{X}||\mathcal{Y}|\\
	=&H(Y|X)+\delta\sum_{x\in\mathcal{X}}(\log p(x)-1)-\delta\sum_{(x,y)\in\mathcal{X}\times\mathcal{Y}}(1-\log p(x,y)-\frac{2}{np(x,y)})\\
	&-\frac{1}{n}\left(\sum_{(x,y)\in\mathcal{X}\times\mathcal{Y}}(\log p(x,y)+1)+\log n |\mathcal{X}||\mathcal{Y}|\right)\\
	&\leq H(Y|X)-\eta(n,\delta)
	\end{align}
$$

where (a) is the Strling's approximation:
	

$$
\begin{align}

	n\ln n-n< \ln n!<(n+1)\ln(n+1)-n
	\end{align}
$$

and (b), (c) are from the AEP and JAEP, $ \lim\limits_{n\to\infty}\eta(n,\delta)=0 $. Thus the bounds are proved.
\#

* Note: (c)'s bound should be changed into $ (p(x,y)+\delta+\frac{1}{n}) $ when $ \exists x,y ,\quad p(x,y)=1$ because in this case $ \log(p(x,y)+\delta+\frac{1}{n}) $ is positive. The results are the same.}

The CAEP shows that the rate of size of $ |\mathcal{T}_{[XY]_\delta}^n(x^n)| $ approximates $ H(Y|X) $ regardless of $ x^n\in\mathcal{T}_{[X]_\delta}^n  $. As a corollary, we show that such typical $ x^n $ that makes $ \frac{1}{n}|\mathcal{T}_{[Y|X]_\delta^n}(x^n)|\to H(Y|X) $ grows with $ n $ at almost the same rate as the number of typical $ x^n\in\mathcal{T}_{[X]_\delta}^n $

**Lemma 11:**
	Let  

$$
\begin{align}

	\mathcal{S}_{[X]_\delta}^n=\{x^n\in\mathcal{T}_{[X]_\delta}^n: \mathcal{T}_{[Y|X]_\delta}^n(x^n)\neq\emptyset\}
	\end{align}
$$

then 
	

$$
\begin{align}

	&\frac{1}{n}\log|\mathcal{S}_{[X]_\delta}^n|\to H(X),\quad n\to\infty\\
	&\exists \gamma(n)\to 0,\quad\frac{1}{n}\log Pr\{X^n\in\mathcal{S}_{[X]_\delta}^{nC}\}<\gamma
		\end{align}
$$

\#
* Note: From this lemma, we can make confusion on the $ \mathcal{S}_{[X]_\delta}^n $ and $ \mathcal{T}_{[X]_\delta}^n $ as they have the same asymptotic property in exponential sense.}
**Proof:**
	The proof is intuitively and techniquely obvious, omitted.
\#
The JAEP and CAEP for 3 or more RVs is similarly defined and proved, we skip the relation.

## The relations of Typicality and SHannon's Inequalities
The typicality gives us an asymptotic perspective on the meaning of Shannon's measures. Correspondingly, it is highly related to the Basic inequalities.

**Example 4:**
	Consider 3 Rvs $ X,Y,Z $. 
	

$$
\begin{align}

	 &(x^n,y^n,z^n)\in\mathcal{T}_{[XYZ]_\delta^n}\\
	 \stackrel{\text{Consistency}}{\Longrightarrow}&(x^n,z^n)\in\mathcal{T}_{[XZ]_\delta^n},\quad (y^n,z^n)\in\mathcal{T}_{[YZ]_\delta^n}\\
	 \stackrel{\text{CTypical}}{\Longrightarrow}&(x^n)\in\mathcal{T}_{[X|Z]_\delta^n}(z^n),\quad (y^n)\in\mathcal{T}_{[Y|Z]_\delta^n}(z^n)\\
	 \Longrightarrow & \mathcal{T}_{[XY|Z]_\delta^n}(z^n)\subseteq \mathcal{T}_{[X|Z]_\delta^n}(z^n)\times\mathcal{T}_{[Y|Z]_\delta^n}(z^n)\\
	 \Longrightarrow & |\mathcal{T}_{[XY|Z]_\delta^n}(z^n)|\leq |\mathcal{T}_{[X|Z]_\delta^n}(z^n)||\mathcal{T}_{[Y|Z]_\delta^n}(z^n)|\\
	 \Longrightarrow & \frac{1}{n}\log |\mathcal{T}_{[XY|Z]_\delta^n}(z^n)|\leq \frac{1}{n}\log|\mathcal{T}_{[X|Z]_\delta^n}(z^n)|+\frac{1}{n}\log|\mathcal{T}_{[Y|Z]_\delta^n}(z^n)|\\
	 \Longrightarrow & H(X,Y|Z)-\epsilon_1\leq H(X|Z)+\epsilon_2+ H(Y|Z)+\epsilon_3\\
	 \stackrel{n\to\infty, \epsilon_1,\epsilon_2,\epsilon_3\to 0}{\Longrightarrow}&H(X,Y|Z)\leq H(X|Z)+ H(Y|Z)
	\end{align}
$$
 
\#
A customized idea is summarized as:

*  write the inequality in the form of (conditional) entropy;
*  Use the jointly typical set and the property;
*  Define the conditional Joint typical set;
*  Give the including relation of the typical sets;
*  Use AEP to transform the including relation of sets to the inequality relation of rates;
*  limit $ n $ to infinity, get the corresponding Shannon's Inequalities.
