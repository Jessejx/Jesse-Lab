# Frequentist vs. Bayesian Approaches in Machine Learning
本节，我将简单介绍Bayesian派与频率派的区别与联系，希望你喜欢

## Frequentist
Maximum Likelihood Estimation, MLE
$$
\begin{align*}
\hat{\theta} &=\underset{\theta}{\arg \max } \mathrm{P}(X \mid \theta) \\
    &=\underset{\theta}{\arg \max } \prod_{i=0}^n \mathrm{P}\left(x_i \mid \theta\right) \\
    &=\underset{\theta}{\arg \max } \sum_{i=0}^n \log \mathrm{P}\left(x_i \mid \theta\right)
\end{align*}
$$

极大似然估计，估计似然函数。给定$\theta$，找到使$\theta$最大的值， （对应神经网络CNN、参数是$\theta$，输出是$x$，不断的给CNN输入数据），通过统计的方法找到$\theta$是多少.
